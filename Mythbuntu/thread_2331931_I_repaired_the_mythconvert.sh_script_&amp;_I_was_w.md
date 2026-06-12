---
title: "I repaired the mythconvert.sh script &amp; I was wondering if there's a way to upd8 wiki"
date: 2016-07-26
forum: Mythbuntu
---

### Post by Espryon on 2016-07-26
Mythconvert.sh i.e. [https://www.mythtv.org/wiki/Mythconvert](https://www.mythtv.org/wiki/Mythconvert) , the old script posted does not work because of unary operators not quoted correctly, that most installs by default use root to access the mysql database and the password the user sets on the main account, and improper use of environment variables i.e. not "0" but, $0 .

```
#!/bin/bash

###################################################
#
# mythconvert.sh
# A utility to convert recordings from mythtv as a user job
# using HandbrakeCLI
#
# Dominique Tardif
# March 2013
#
###################################################
#arguments order:
# 1 - %JOBID% : job id as given by mythtv
# 2- %DIR%: input directory as given by mythtv
# 3- %FILE%: input file as given by mythtv
# 4- %TITLE%: show title as given by mythtv
# 5 - %SUBTITLE%: show subtitle as given by mythtv -> this is optionnal
#	In the absence of a subtitle, could also be a handbrake preset in form of --preset=\"PRESET\"
# 6 - Handbrake preset -> this is optionnal
#	Should be of form --preset=\"PRESET\"


###################################################
#
# Script configuration section
#
###################################################

#Values for transcoder
#
# niceValue : nice value for encoding job. Default: 15
# transcodeOptions :   command line options for handbrake.
#				This will be overwritten if a handbrake preset is specified with the command --preset=\"PRESET\"
#				Be sure to escape " as written : \"
#				Default: --format mkv --two-pass --turbo --vb 1500
# outputExtension: Desired output file extension, without period. Default: mkv
niceValue="15"
transcodeOptions="--format mkv --two-pass --turbo --vb 1500"
outputExtension="mkv"

#Change permissions of output file if desired, set to 1 to enable
chmodON="0"
chmodMOD="644"

#Folder for output - do not add trailing slash
outputFolder="/media/RAID/mythtv/streaming/"

#Enter mythtv database information here
dbServer="localhost"
dbUser="root"
dbPwd="password12345"
dbName="mythconverg"

###################################################
#
# Script internal variables - do not edit
#
###################################################
id="$1"
preset='(--preset=".*")'
inputFile="$2/$3"
outputFile=""
title="$4"
subtitle="$5"

statusStarting=3
statusRunning=4
statusStopping=5
statusPaused=6
statusErroring=8
statusDone=256
statusFinished=272
statusErrored=304

currentCommand=""
newCommand=""
encodePID=""

# getCommand - get command set by mythtv in jobqueue table
# Parameters : none
getCommand()
{
	newCommand=$(echo "SELECT cmds FROM jobqueue WHERE id='$id'" | mysql -h $dbServer -u $dbUser --password=$dbPwd $dbName | tail -1)
}

# setStatus - sets current job status in jobqueue table
# Parameters: takes one parameter as integer - see internal variables for status definitions
setStatus()
{
	status=$1
	echo "UPDATE jobqueue SET status='$status' WHERE id='$id'" | mysql -h $dbServer -u $dbUser --password=$dbPwd $dbName
}

# updateComment - changes the comment for the running job in jobqueue table
# Parameters: takes one parameter as string 
updateComment()
{
	comment=$1
	echo "UPDATE jobqueue SET comment='$comment' WHERE id='$id'" | mysql -h $dbServer -u $dbUser --password=$dbPwd $dbName
}

# startEncode - starthe actual encoding when getCommand returns 0
# Parameters: none 
startEncode()
{
	setStatus $statusStarting
	updateComment "starting mv2vids job with id $id"
	nice -n $niceValue HandBrakeCLI $transcodeOptions	-i "$inputFile" -o "$outputFile" > /tmp/mv2vids.log 2> /tmp/mv2vids.err.log &
	encodePID=$!
	setStatus $statusRunning
	updateComment "Job id $id is running"
}

# stopEncode - stop the encoding when getCommand returns 4
# Parameters: none 
stopEncode()
{
	setStatus $statusStopping
	updateComment "stoping mv2vids job with id $id"
	kill -15 $encodePID
	tryKill=$?
	if [ $tryKill -eq -1 ]
		then error "Could not cleanly terminate process"
	fi
	rm /tmp/mv2vids.log
	setStatus $statusDone
	updateComment "Job stopped"
}

# pause - pause the encoding when getCommand returns 1
# Parameters: none 
pause()
{
	kill -19 $encodePID
	setStatus $statusPaused
	updateComment "Job id $id is paused"
}

# resume - resume the encoding when getCommand returns 2
# Parameters: none 
resume()
{
	setStatus $statusStarting
	updateComment "Resuming mv2vids job with id $id"
	kill -18 $encodePID
	setStatus $statusRunning
	updateComment "Job id $id is running"
}

# error - exits script when error
# Parameters: takes one string to send back to mythtv as error message
error()
{
	setStatus $statusErroring
	updateComment "mv2vids job with id $id encountered an error"
	setStatus $statusErrored
	updateComment "$1"
	if [ -n "$encodePID" ]
		then kill -9 $encodePID
	fi
	#Un-comment next line to remove log file
	#Kept by default to see if there is an error
	#rm /tmp/mv2vids.log
	exit 1
}

# restartEncode - stops current job and restart it
# Parameters: none
restart()
{
	setStatus $statusStopping
	updateComment "mv2vids job with id $id is stoping for a restart"
	stopEncode
	startEncode
}

# main - controls job flow
# Parameters: takes two parameters
# 1 - Recording title 
# 2 - Recording subtitle

main()
{
	getCommand
	currentCommand=$newCommand
	if [ "$currentCommand -eq $0" ] #Verify if job is set to run in mythtv database
		then 
		if [ -n "$2" ] #Verify if there is a subtitle attached to the job, set outputFile accordingly
			then
			outputFile="$outputFolder/$1 - $2.$outputExtension"
			startEncode
		else
			if [ -n "$1" ]
				then
				outputFile="$outputFolder/$1.$outputExtension"
				startEncode
			else
				error "Not enough parameters, should have ID,DIR,FILE,TITLE,SUBTITLE(optional). Check job configuration in mythtv"
			fi
		fi
	else error "Job $id not set to run in jobqueue"
	fi
	
	#Main control loop - checks if process is running and if command change in mythtv database
	
	kill -0 $encodePID
	jobRunning=$?
	while [ $jobRunning -eq 0 ]
	do
		getCommand
		currentCommand=$newCommand
		case "$currentCommand" in
			"0" )
			progress=$(strings /tmp/mv2vids.log | tail -1 | grep "" | tail -1)
			updateComment "$progress"
			;;
			"4" )
			stopEncode
			exit 0
			;;
			"1" )
			pause
			;;
			"2" )
			resume
			;;
		esac
		sleep 10
		kill -0 $encodePID
		jobRunning=$?
	done
	setStatus $statusFinished
	updateComment "Job successful"
	if [ "$chmodON" -eq "1" ]
		then chmod $chmodMOD $outputFile
	fi
	exit 0
	
}

#Check is user entered --preset and overwrite default transcodeOptions
if [ -n "$6" ]
	then
	if [[ $6 =~ $preset ]]
		then transcodeOptions="$6"
	fi
else
	if [ -n "$5" ]
		then
		if [[ $5 =~ $preset ]]
			then
			transcodeOptions="$5"
			subtitle=""
		fi
	fi	
fi	

#This line is simply to start the main function, passing title and subtitle as arguments
main "$title" "$subtitle"


```

---

### Post by Ubu_Fester on 2016-12-07
Do you run this as a job within mythbuntu, or do you run this at the terminal?

---

### Post by Espryon on 2017-01-29
> **Ubu_Fester said:**
> Do you run this as a job within mythbuntu, or do you run this at the terminal?

Either or. I was so dismayed by the idea though reading the forums this morning that the mythbuntu project as a distro has been abandoned. Kinda depressing tbh... I wonder how long the distro will last without the development of it continuing. Like.. what are the alternatives to mythbuntu?

---

