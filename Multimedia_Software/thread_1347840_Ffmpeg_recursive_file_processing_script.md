---
title: "Ffmpeg recursive file processing script"
date: 2009-12-06
forum: Multimedia Software
---

### Post by pablogrb on 2009-12-06
I wrote an bash script for file processing (mainly to do format conversion) using ffmpeg but I think there are better and more elegant ways to do it. It's designed to work recursively and using multiple simultaneous ffmpeg processes (ideally, one per processor).

I would greatly appreciate any improvements any of you can make and hope that someone finds it useful.

```

#!/bin/bash
# Welcome message
echo "==========================================================================="
echo "Recursive transcoder with space handling"
echo "Requires ffmpeg + unrestricted libraries"
echo "Uses gnome-terminal for background process monitoring"
echo
echo "2009 - Pablo García - V a0.2"
echo "Usage: recffmpeg [threads] [\"ffmpeg-parameters\"] [input-ext] [output-ext]"
echo "=========================================================================="

# Read the threads parameter
if [ -z $1 ]; then
	exit
else
	threads=$1
	echo
	echo "Using $threads threads"
	echo
fi

# Read the rest of the parameters
ffpars=$2
ffext=$3
ffext2=$4

# Recursive file renaming
find . -type f -name "*.$ffext" -exec rename 's/ /_/g' '{}' \;

# Loop by reverse file size
find . -type f -name "*.$ffext" -exec du -sk '{}' \; | sort -n > find.log

# Do a line count in the log file
count=`wc -l find.log | awk '{print $1}'`

# Loop every $threads
for i in $(seq 1 $threads $count); do
	
#	Loop for trough the first $threads - 1 files
	for j in $(seq 1 $((threads - 1))); do

		k=$((i + $j - 1))
		if (($k > $count)); then
			echo
			echo "==========================================================================="
			echo "Transcoding finished"
			echo "$count files processed"
			echo "==========================================================================="
			exit
		fi
		name=`sed -n ${k}p find.log`
		cname=`echo ${name#*"./"}`

		echo "---------------------------------------------------------------------------"
		echo "Processing file number $k $cname"
		echo "---------------------------------------------------------------------------"

#		=====================================================
#		Use the ffmpeg library to transcode to avi in a new terminal window
		gnome-terminal -e "ffmpeg -i $cname $ffpars ${cname%$ffext}$ffext2" &
#		=====================================================

	done
	
#	Process the final file in the foreground
	nexti=$((i + $threads - 1))
	if (($nexti > $count)); then
		echo
		echo "==========================================================================="
		echo "Transcoding finished"
		echo "$count files processed"
		echo "==========================================================================="
		exit
	fi
	name=`sed -n ${nexti}p find.log`
	cname=`echo ${name#*"./"}`
	echo "---------------------------------------------------------------------------"
	echo "Processing file number $nexti $cname"
	echo "---------------------------------------------------------------------------"

#	=====================================================
#	Use ffmpeg library to transcode to avi
	ffmpeg -i $cname $ffpars ${cname%$ffext}$ffext2
#	=====================================================

done

# Erase the log file
rm find.log

# Recursive file re-renaming
find . -type f -name "*.$ffext" -exec rename 's/_/ /g' '{}' \;
find . -type f -name "*.$ffext2" -exec rename 's/_/ /g' '{}' \;

```

NOTE: The code in the attachment is dated, spelling errors and old comments were removed in the posted code.

---

### Post by kingaaronj on 2011-09-13
Just found this little gem.  Gotta say this is very very handy!

Thanks for all the work you put into this. :)

---

