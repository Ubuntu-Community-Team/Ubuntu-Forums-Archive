---
title: "Handbrake CLI script"
date: 2012-03-15
forum: Multimedia Software
---

### Post by loofi on 2012-03-15
Hi,

I'm trying to get a script to encode everything within a direcory to mp4. The script works fine however I would also like to test against more than just "avi" as input extension. Example: mkv and others.

Thanx to Derrek Young for the script!

Can anyone help me with how to test against more than one extension in this script?

[SIZE="2"]```

#!/bin/sh

###############################################################################
#
# Script to recursively search a directory and batch convert all files of a given
# file type into another file type via HandBrake conversion.
#
# To run in your environment set the variables:
#   hbcli - Path to your HandBrakeCLI
#
#   source_dir - Starting directory for recursive search
#
#   input_file_type - Input file type to search for
#
#   output_file_type  - Output file type to convert into
#
#
# Change log:
# 2012-01-08: Initial release.  Tested on Mac OS X Lion.
#
###############################################################################

hbcli=/Applications/HandBrakeCLI/HandBrakeCLI
source_dir="/Movies"
input_file_type="avi"
output_file_type="m4v"

echo "# Using HandBrakeCLI at "$hbcli
echo "# Using source directory "$source_dir
echo "# Converting "$input_file_type" to "$output_file_type

# Convert from one file to another
convert() {
	# The beginning part, echo "" | , is really important.  Without that, HandBrake exits the while loop.
	echo "" | $hbcli -i "$1" -o "$2" --preset="Universal";
}

# Find the files and pipe the results into the read command.  The read command properly handles spaces in directories and files names.
find $source_dir -name *.$input_file_type | while read in_file
do
        echo "Processing…"
	echo ">Input  "$in_file

	# Replace the file type
	out_file=$(echo $in_file|sed "s/\(.*\.\)$input_file_type/\1$output_file_type/g")
	echo ">Output "$out_file

	# Convert the file
	convert "$in_file" "$out_file"

	if [ $? != 0 ]
        then
            echo "$in_file had problems" >> handbrake-errors.log
        fi

	echo ">Finished "$out_file "\n\n"
done

echo "DONE CONVERTING FILES"

```[/SIZE]

---

### Post by papibe on 2012-03-16
Hi loofi.

I've done similar scripts in the past and I have a few tips.

First of all, this structure sometimes may cause problems:
```
find $source_dir -name *.$input_file_type | while read in_file
do
    ...
    ...
done
```
Our forum's bash expert extraordinaire sisco311 recommended this other structure, and it's been working really well for me:
```
while IFS= read -d '' -r in_file
do
    ...
    ...
done< <(find $source_dir -name *.$input_file_type -print0)
```
Besides a tighter integration between 'while' and 'find', it is also safer when filenames have none standard characters on them.

Now to your concern ;)

If you can make a list of all kind of video files you have, you can use this kind of 'find':
```
find $source_dir -iname **'*.mkv'** -o -iname **'*.mp4'** -o -iname **'*.avi'**
```
where
[INDENT]-iname is like -name but case insensitive, so it could find both file.mkv and FILE.MKV, for instance.
-o is a logical 'or'.[/INDENT]
Now a special case. Let's say you have a enormous amount of video files so listing all possible extensions is, in itself, a heavy task.

Facing a similar situation I've used a command line tool called 'mediainfo'. [Here]("http://ubuntuforums.org/showthread.php?t=1941003&highlight=mediainfo")'s how to install it, and [here]("http://ubuntuforums.org/showthread.php?t=1941386")'s an example of how to use it on a script.

This is an example on how to find all video files:
```
while IFS= read -d '' -r in_file
do
    video=$(mediainfo "$in_file" | grep -i video > /dev/null)

    # if the previous expression returned 0, then it is a video file.
    if [ $? = 0 ]; then
        echo "Processing&#8230;"
        ...
    fi

done< <(find $source_dir -type f -print0)
```
Now, this is very slow because every file is being read to determine if it is a valid video file. What I've done recently is do the job on 2 scripts: first get the list of videos into a temp file, and then run the main loop reading from the file.

This would be the first script:
```
while IFS= read -d '' -r in_file
do
    if (mediainfo "$in_file" | grep -i video > /dev/null); then
        printf "%s\0" "$in_file" >> **video_list.txt**
    fi

done< <(find $source_dir -type f -print0)
```
And then in another script:
```
while IFS= read -d '' -r in_file
do
    echo "Processing&#8230;"
    ...

done< **./video_list.txt**
```

I hope that point you in the right direction.
Tell us if you need more help with those scripts.
Regards.

---

### Post by Dmka on 2012-08-12
This script will allow the batch to be resumed. It also check to see file the output file is valid because HandbrakeCLI can not be replied upon to give a valid return value.

The script takes a file containing a list of video file names to be encoded as a parameter eg.

```

$ ./transcode.sh videos.txt

```



```

#!/bin/bash

# Transcode a list of video files to mp4/h.264
# The result is output in-place and a .old suffix is added to input video file 

hbcli=/usr/bin/HandBrakeCLI
mi=/usr/bin/mediainfo

declare out_file

if [ -z "$1" ]
then
    echo "Usage: $(basename $0) Filename"
    echo ""
    echo "An input file can be created using find"
    echo "eg. find /home/dimitry/Videos/ -name *.avi | sort > video_list.txt"    
    exit 0
fi

trap on_exit SIGINT SIGQUIT SIGHUP SIGTERM

function on_exit() {
    echo "aborted"
    rm -f "$out_file"
    exit 1
}

while read in_file
do
    if [ -f "$in_file" ]
    then
        echo "Processing…"
        echo ">Input $in_file"

        # remove file extension
        base_file=$(echo "$in_file" | sed 's/\(.*\)\..*/\1/')

        out_file="$base_file.mp4.tmp"
        
        echo ">Output $out_file"

        # encode file
        echo "" | $hbcli -i "$in_file" -o "$out_file" --preset="Universal"

        # check output is valid
        if $mi "$out_file" | grep -q "Format[ ]*: AVC"
        then
            mv "$out_file" "$base_file.mp4"
            mv "$in_file" "$in_file.old"
        else
            rm -f "$out_file"
            echo "$in_file had problems" >> "$(basename $0).log"
        fi

        echo ">Finished $in_file"
    fi
done < $1

```

---

