---
title: "bash script - ftp sync single file - using ftp size and mdtm"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by sdaau on 2009-09-13
Hi all, 

I was looking for a while for a simple command line 'ftp sync' - i.e. something that would use plain ftp, accept local and remote path to a file, compare sizes and timestamps, and ask for appropriate action (download or upload). 

Since I couldn't find anything like that, I managed to write something - and as I didn't find it trivial, here is the script, shown below. Simply save the contents as a text file called "ftp-sync-file", and make it executable ```
chmod +x ftp-sync-file
``` from command line). The script can then be called as:

```
./ftp-sync-file /path/to/local-file.txt ftp.remotesite.com /remote/path/on/server ftp-username-111 
```The local filename is taken as the filename reference. The script also uses bc (for bash calculation) and lftp (simply because it provides some command line feedback while up/downloading), if you don't have them, you'll have to install them (```
sudo apt-get install bc lftp
``` from command line).

I used plenty of references to write this - some of the code is more-less directly copypasted from examples - so those are included below the code as well.. 

Well, hope some may find this useful, 
Cheers !! :D 

```

# filename: ftp-sync-file
# cannot use directly username in ftp: user@ftp.site.net: Unknown host

# FUNCTIONS
function match_index()
{
  local pattern=$1
  local string=$2  
  local result=${string/${pattern}*/}

  [ ${#result} = ${#string} ] || echo ${#result}
}

function bytesShow()
{
    # use bc for bash calculation
    local inbytes=$1
    local kibi=`echo "scale=2; $inbytes/1024" | bc` # ((kibi=inbytes/1024))
    local mebi=`echo "scale=2; $inbytes/(1024^2)" | bc` # ((mebi=kibi/1024))
    local gibi=`echo "scale=2; $inbytes/(1024^3)" | bc` # ((gibi=mebi/1024))
    echo $kibi KiB, $mebi MiB, $gibi GiB
}

function MdtmToUnixTimeString()
{
    #input mdtm 20061231240000 
    #unix date 2006-12-31 24:00:00 CEST - format accepted by date
    local mdtm=$1 
    local mdtm_unixdatestr=`echo "$mdtm" | sed -n -e "s_\(....\)\(..\)\(..\)\(..\)\(..\)\(..\)_\1-\2-\3 \4:\5:\6 UTC_p"`
    local mdtm_unixstr=`date --date="$mdtm_unixdatestr"`
    echo $mdtm_unixstr
}

function MdtmToUnixSeconds()
{
    #input mdtm 20061231240000 
    #unix date 2006-12-31 24:00:00 CEST - format accepted by date
    local mdtm=$1 
    local mdtm_unixdatestr=`echo "$mdtm" | sed -n -e "s_\(....\)\(..\)\(..\)\(..\)\(..\)\(..\)_\1-\2-\3 \4:\5:\6 UTC_p"`
    local mdtm_unixsecs=`date --date="$mdtm_unixdatestr" +%s`
    echo $mdtm_unixsecs
}


# START

# call with ./ftp-sync-file lpathfile rsite rdir ruser - complain on less than four arguments
: ${4?"
Usage: $0 lpathfile rsite rdir ruser"}

# just to init sudo - if needed
# sudo pwd

lpathfile=$1 # "./thisfile.txt"
lfulpathfile=$(readlink -f $lpathfile) # `readlink -f $lpathfile`
filename=$(basename $lfulpathfile) # only filename "thisfile.txt"
lfulpath=$(dirname $lfulpathfile) 

rsite=$2 # "ftp.site.com"
rdir=$3 # "/www/path/to/dir"
ruser=$4 # "usertest"
# rpassword="userpassword"

## prompt for FTP password
echo -n "FTP password for user $ruser: "

stty -echo
read rpassword
stty echo

echo ""         # force a carriage return to be output
# echo You entered $rpassword

echo ""
echo "Checking remote file - connecting ftp: $ruser @ $rsite..."

## get verbose multiline ftp response in $response variable 
## ask for size (needs passive) and mdtm of file
## both mdtm and size return 213 answer 
response=`ftp -pnv $rsite <<EOF 
  quote USER $ruser
  quote PASS $rpassword

  cd $rdir
  pwd
  dir
  size $filename 
  modtime $filename
  quote mdtm $filename
  quit
EOF`

# mutliline variable must be quoted to see the breaks 
# echo Response is: "$response" 

# now parse response

# the line entry for the file as result of dir - will contain both file size and human readable date
read rdirline <<EOF
`echo "$response" | grep $filename`
EOF

# there will now be several 213 ftp responses here - so multiline grep (assign to variable):
resp213=`echo "$response" | grep 213 `

# parse the grepped 213 responses ($resp213) into an array ($resp213array).. 
# use IFS - Input File Separator
oldifs=$IFS
IFS='
'
i=1 # the first array variable is at index 1
for subln in $resp213; do
    resp213array[$i]=$subln
    let i++
done
IFS=$oldifs

# echo resp213array: ${resp213array
[*]}
rsizeline=`echo ${resp213array[1]}`
rmdtmline=${resp213array[2]}

# rcurloc also '257 '
read rcurloc <<EOF
`echo "$response" | grep "current location" `
EOF

# take remote file size to be sizeline from 4th character onwards ('213 3592192'), same for remote file  mdtm
rfsize=${rsizeline:4}
rfmdtm=${rmdtmline:4}

# get remote date from dir listing
indexofsize=$(match_index "$rfsize" "$rdirline") # `expr index "$rdirline" "$rfsize"`works only with first char
lengthofsize=${#rfsize}
indexofname=$(match_index "$filename" "$rdirline") #`expr index "$rdirline" "$filename"`works only with first char
indexofdate=$((indexofsize+lengthofsize))
rdirdate=${rdirline:$((indexofdate+1)):$((indexofname-indexofdate-1))}

# get local file data
lfsizeline=`du -h --bytes $lpathfile`
tabber="    "
indexoftab=`expr index "$lfsizeline" "$tabber"`
lfsize=${lfsizeline:0:$((indexoftab-1))}

# to get the same datetime format as FTP MDTM, use  --time-style="+%Y%m%d%H%M%S" with ls
# as ftp server date time - --time-style="+%e,%b %Y"
ldirline=`ls -l --time=ctime --time-style="+%b %e %Y %H:%M %Z" $lfulpathfile`
lmdtmline=`TZ="UTC" ls -l --time=ctime --time-style="+%Y%m%d%H%M%S" $lfulpathfile`

# get local date from dir listing
indexofsize=$(match_index "$lfsize" "$ldirline") 
lengthofsize=${#lfsize}
indexofname=$(match_index "$lfulpathfile" "$ldirline") 
indexofdate=$((indexofsize+lengthofsize))
ldirdate=${ldirline:$((indexofdate+1)):$((indexofname-indexofdate-1))}

# get local UTC mdtm-like timestamp from dir listing
indexofsize=$(match_index "$lfsize" "$lmdtmline") 
lengthofsize=${#lfsize}
indexofname=$(match_index "$lfulpathfile" "$lmdtmline") 
indexofdate=$((indexofsize+lengthofsize))
lfmdtm=${lmdtmline:$((indexofdate+1)):$((indexofname-indexofdate-1))}

# compare sizes
if [ $lfsize -eq $rfsize ]
then
    lsizestatus="equal"
    rsizestatus="equal"
elif [ $lfsize -gt $rfsize ]
then
    lsizestatus="BIGGER"
    rsizestatus="smaller"
else
    lsizestatus="smaller"
    rsizestatus="BIGGER"
fi

# generate sizes in bytes with thousands separator
rfsizeb=`echo $rfsize | sed -r ':L;s=\b([0-9]+)([0-9]{3})\b=\1,\2=g;t L'`
lfsizeb=`echo $lfsize | sed -r ':L;s=\b([0-9]+)([0-9]{3})\b=\1,\2=g;t L'`
# generate sizes in other units
rfsizec=$(bytesShow "$rfsize") 
lfsizec=$(bytesShow "$lfsize") 

# compare dates
lfmdtmus=$(MdtmToUnixSeconds "$lfmdtm")
rfmdtmus=$(MdtmToUnixSeconds "$rfmdtm")

# compare sizes - more seconds from 1970 = file is newer
if [ $lfmdtmus -eq $rfmdtmus ]
then
    ltimestatus="equal"
    rtimestatus="equal"
elif [ $lfmdtmus -gt $rfmdtmus ]
then
    ltimestatus="NEWER"
    rtimestatus="older"
else
    ltimestatus="older"
    rtimestatus="NEWER"
fi

# give suggestion
if ( [[ $lsizestatus = "BIGGER" ]] && [[ $ltimestatus = "NEWER" ]] )  
then
    suggest="upload (local to remote)"
elif ( [[ $rsizestatus = "BIGGER" ]] && [[ $rtimestatus = "NEWER" ]] )  
then
    suggest="download (remote to local)"
else
    suggest="no suggestion."
fi

# report
echo "
        FILE: $filename

remote location:    $rcurloc
remote size:        $rfsizeb bytes ($rfsizec)
remote dir.time:    $rdirdate 
remote mod.time:    $rfmdtm (UTC - MDTM); 
            $rfmdtmus sec epoch - $(MdtmToUnixTimeString $rfmdtm);

local location:    $lfulpath
local size:    $lfsizeb bytes ($lfsizec)
local dir.time:    $ldirdate 
local mod.time:    $lfmdtm (UTC); 
        $lfmdtmus sec epoch - $(MdtmToUnixTimeString $lfmdtm);

Local file size is $lsizestatus than remote file size ( remote file size is $rsizestatus ).
Local file time is $ltimestatus than remote file time ( remote file time is $rtimestatus ).

Suggestion: $suggest.
"
choice=3
echo -n "Your choice ([0] cancel, [1] upload {loc -> rem}, [2] download {rem -> loc})? "  

while [ $choice -eq 3 ]; do
    read choice #for no wait: read -n 1 choice
done

echo -$choice-;

case "$choice" in
'1')
echo "Uploading local to remote file.

PUT:: $lfulpathfile to $rsite:$rdir/$filename file.
"
echo lftp -u $ruser,$rpassword -e "lcd $lfulpath; cd $rdir; pwd; lpwd; put $filename; bye" $rsite
;;
'2')
echo "Downloading remote to local file.

GET:: $rsite:$rdir/$filename to $lfulpathfile file.
"
echo lftp -u $ruser,$rpassword -e "lcd $lfulpath; cd $rdir; pwd; lpwd; get $filename; bye" $rsite
;;
*)
echo "Cancelling."
;;
esac

echo "Done."


```
And below please find some references: 


```

# [http://stackoverflow.com/questions/1234852/getting-the-index-of-the-substring-on-solaris](http://stackoverflow.com/questions/1234852/getting-the-index-of-the-substring-on-solaris)
# [http://www.askdavetaylor.com/prompting_users_for_passwords_in_a_shell_script.html](http://www.askdavetaylor.com/prompting_users_for_passwords_in_a_shell_script.html)
## have to be in verbose mode to show result of SIZE command!! size response is '213 '
## [http://www.unix.com/shell-programming-scripting/53674-how-pipe-output-here-document.html](http://www.unix.com/shell-programming-scripting/53674-how-pipe-output-here-document.html)
## [http://www.unixguide.net/unix/bash/E4.shtml](http://www.unixguide.net/unix/bash/E4.shtml) - must have backticks for executing nested here document
## * so use ftp size with verbose and grep 213  (`ftp -nv $rsite <<EOF | grep 213 )  ....        OR
## * use ftp dir and grep rfile (`ftp -pnv $rsite <<EOF | grep $rfile )
## using read response is restricted to single line

## problem with "500 I won't open a connection to 192.168..." for opening second ftp connection...
## check ...
# ps axf | grep ftp
# sudo netstat -lntp | grep ":22" # shows nothing strange
# [http://unstableme.blogspot.com/2008/06/bash-wait-command.html](http://unstableme.blogspot.com/2008/06/bash-wait-command.html)
# wait  # ${!} 
## In fact, the problem "500 I won't open a connection to 192.168..."  is with using ls/dir commands 
## [http://forums.powweb.com/showthread.php?t=45714](http://forums.powweb.com/showthread.php?t=45714)
## - if behind a router, must open passive mode for it: fpt -pnv

## read will only capture a single line - so only useful with inline grep
# read response << HERE
# `ftp -nv $rsite <<EOF | grep 213 
  # quote USER $ruser
  # quote PASS $rpassword
  # cd $rdir
  # size $rfile 
  # pwd
  # quit
# EOF` 
# HERE

## for multiline use direct assignment  (as 'read' will only capture a single line anyway)
# mutliline variable must be quoted to see the breaks [http://stackoverflow.com/questions/613572/capturing-multiple-line-output-to-a-bash-variable](http://stackoverflow.com/questions/613572/capturing-multiple-line-output-to-a-bash-variable)
# [https://www.linuxquestions.org/questions/programming-9/split-a-string-on-newlines-bash-313206/](https://www.linuxquestions.org/questions/programming-9/split-a-string-on-newlines-bash-313206/)
# [http://www.linuxquestions.org/questions/linux-software-2/bash-split-by-newline-617175/](http://www.linuxquestions.org/questions/linux-software-2/bash-split-by-newline-617175/)
# [http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

## this with echo piping into while parses - but the array variable contents are unavailable outside the loop
# i=1 # the first array variable is at index 1
# echo "$resp213" | while read line
# do 
  # resp213array[$i]=$line
  ## echo    test: ${resp213array[$i]} ${resp213array
[*]}
  # let i++
# done 

# numeric manipulation [http://www.linuxquestions.org/questions/programming-9/converting-string-to-integer-in-bash-608444/](http://www.linuxquestions.org/questions/programming-9/converting-string-to-integer-in-bash-608444/)
# $ a=15
# $ b=14
# $ echo $((a+b))
# 29
# $ echo $((a))+$((b))
# 15+14
# string manipulation dirname basename [http://linuxgazette.net/issue18/bash.html](http://linuxgazette.net/issue18/bash.html)
# string manipulation [http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/refcards.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/refcards.html)
# string manipulation [http://www.linuxquestions.org/questions/linux-newbie-8/bash-string-manipulation-help-670627/](http://www.linuxquestions.org/questions/linux-newbie-8/bash-string-manipulation-help-670627/)

# to get the same datetime format as FTP MDTM, use  --time-style="+%Y%m%d%H%M%S" with ls
# as ftp server date time - --time-style="+%e,%b %Y"
# [http://www.unix.com/shell-programming-scripting/19685-last-modified-date-2.html](http://www.unix.com/shell-programming-scripting/19685-last-modified-date-2.html)
# mdtm gives in GMT - [https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1252828241847+28353475&threadId=1340784](https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1252828241847+28353475&threadId=1340784)
# [https://www.linuxquestions.org/questions/linux-newbie-8/ls-mtime-137259/](https://www.linuxquestions.org/questions/linux-newbie-8/ls-mtime-137259/)
# [http://www.wlug.org.nz/TimeNotes](http://www.wlug.org.nz/TimeNotes)
# $ date +%s
# 1252829069
# $ date --date="1970-01-01 `date +%s` secs UTC"
# Sun Sep 13 10:05:02 CEST 2009
# $ date +%Y
# 2009
# date +%Y-%M
# 2009-08
# if ( [[ $tt = "test" ]] && [[ $tt = "test" ]] ) ; then echo true; else echo false; fi
# [http://www.linuxquestions.org/questions/linux-general-1/bash-how-to-get-time-in-seconds-elapsed-since-creation-of-a-file-178335/](http://www.linuxquestions.org/questions/linux-general-1/bash-how-to-get-time-in-seconds-elapsed-since-creation-of-a-file-178335/)
## To force UTC, simply set $TZ to UTC: TZ="UTC" ls <options>. This will set $TZ to UTC just for the duration of this command.

# add thousand separator [http://unix.derkeiler.com/Newsgroups/comp.unix.shell/2006-10/msg00698.html](http://unix.derkeiler.com/Newsgroups/comp.unix.shell/2006-10/msg00698.html)
# Format numbers using bash? - LinuxQuestions.org - [http://www.linuxquestions.org/questions/programming-9/format-numbers-using-bash-672031/](http://www.linuxquestions.org/questions/programming-9/format-numbers-using-bash-672031/)
# Perl vs. bash code - number of lines - LinuxQuestions.org - [http://www.linuxquestions.org/questions/programming-9/perl-vs.-bash-code-number-of-lines-534142/](http://www.linuxquestions.org/questions/programming-9/perl-vs.-bash-code-number-of-lines-534142/)
# Cool Solutions: Bash - Floating Point Math at the Shell - [http://www.novell.com/coolsolutions/tools/17043.html](http://www.novell.com/coolsolutions/tools/17043.html)
# convert date format YYYYMMDD to MM/DD/YYYY - Page 2 - The UNIX and Linux Forums - [http://www.unix.com/shell-programming-scripting/28121-convert-date-format-yyyymmdd-mm-dd-yyyy-2.html](http://www.unix.com/shell-programming-scripting/28121-convert-date-format-yyyymmdd-mm-dd-yyyy-2.html)
# Simple date and time calulation in BASH - The UNIX and Linux Forums - [http://www.unix.com/tips-tutorials/31944-simple-date-time-calulation-bash.html](http://www.unix.com/tips-tutorials/31944-simple-date-time-calulation-bash.html)


```

Edit: Forgot to say that the actual lftp commands in the above code are "echoed" for testing (i.e. 'echo lftp ...'), so remove the word 'echo' from before 'lftp' when you're ready to actually use the script :)

---

### Post by x22 on 2009-09-24
very handy utility
thanks

---

