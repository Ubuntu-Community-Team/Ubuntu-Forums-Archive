---
title: "Ripping, then encoding to multiple formats."
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by Keith_Beef on 2006-12-11
I usually rip any CD I buy to listen to the music as an Ogg file.

A few months ago, I got a pocket mp3 player, and started ripping to lower bitrate mp3 as well. Then I got a Palm tungsten, and thought about using Aeroplay to play a downsampled ogg file.

But I found it clumsy to rip each disc twice, once encoding to ogg and once encoding to a low bitrate mp3.

I looked into using sox or some other script (like ogg2mp3), but wasn't happy for two reasons:
[LIST]
[*]converting from one lossy format to another is not a good thing to do,
[*]using sox to downsample messes up the tags (see [this thread]("http://ubuntuforums.org/showthread.php?t=303791"))
[/LIST]

So I decided to write a little Nautilus script.

Now, when I rip a CD, I tell gript to not delete the wav file after encoding to ogg.

Then, I go into the directory containing the ogg and wav files, I select the wav files and use this script to encode the wav files to mp3.


```
## wav_util
#
# takes a list of selected wav files
#
# loop through the list, for each file it
# looks for a corresponding ogg file.
# It reads the tags from the ogg file and
# uses them as tags as it converts the wav to an mp3.
# 
#
for a in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
	# set the filenames to use
	input_file=${a}
	stem=`echo ${a} | cut -f1 -d"."`
	ogg_file=${stem}.ogg
	output_file=${stem}.mp3
	
	# set the bitrate to use when converting to mp3
	bitrate=64

	# use ogginfo to extract tags
	title=`tagtool --dump ${ogg_file} | grep "title=" | cut -f2 -d"="`
	artist=`tagtool --dump ${ogg_file} | grep "artist=" | cut -f2 -d"="`
	album=`tagtool --dump ${ogg_file} | grep "album=" | cut -f2 -d"="`
	year=`tagtool --dump ${ogg_file} | grep "date=" | cut -f2 -d"="`
	tracknumber=`tagtool --dump ${ogg_file} | grep "tracknumber=" | cut -f2 -d"="`
	genre=`tagtool --dump ${ogg_file} | grep "genre=" | cut -f2 -d"="`

	# write to log file
	echo "read tags from ${ogg_file}" >> wav_util.log
	echo "Title is ${title}" >> wav_util.log
	echo "Artist is ${artist}" >> wav_util.log
	echo "Album is ${album}" >> wav_util.log
	echo "Year is ${year}" >> wav_util.log
	echo "Track is ${tracknumber}" >> wav_util.log
	echo "Genre is ${genre}" >> wav_util.log
	echo "to convert ${input_file}" >> wav_util.log
	echo "into ${output_file}" >> wav_util.log
	echo " " >> wav_util.log
	echo " " >> wav_util.log

	# call lame to encode the wav to an mp3
	/usr/bin/lame -h -b ${bitrate} --tt "${title}" --ta "${artist}"	--tl "${album}" --ty "${year}" --tn "${tracknumber}" --tg "${genre}" ${input_file} ${output_file}

	# delete the old wav file
	# rm ${input_file}

done

```

Calling tagtool six times in order to extract the six tags is definitely wasteful.

But the time this takes, compared to the time spent encoding, is trivial.

Writing to the logfile could be made more elegant, too.


Beef.

---

### Post by alzaf on 2006-12-15
I had just bought a cheap MP3 player and the files I had transcoded from my OGG collection sounded lousy.

Inspired by your script, I amended my python transcode code but I took a different approach. I just used grip to rip the CD's and write the tag info as part of the file name. 

In Grip, you go into Config/Encode/Encoder options and amend the Encode File Format field to  /tmp/%A/%d/%t-%n.%x (this encodes wav files to /tmp folder). You then have to go to the Config/Misc tab and Tick the Do not lowercase filenames and enter () in Characters to no to strip in filenames field.

The script which you save as encode.py is as follows:

```

#! /usr/bin/python2.4

"""
encode.py

Script to encode a folder full to wave files to specified format. The encoding programs used are oggenc 
and lame. 

The music tags are extracted to list from wave filename. The lists contents are as follows:
0 - Track number
1 - Disc title
2 - Year
3 - Genre
4 - Disc artist
5 - Title artist
6 - Title name
"""

import glob
import os

# Constants
BITRATE = 128
ENC_FORMAT = 'MP3'
SOURCE_DIR = '/tmp'


def getEncodeStr(tagList, wavFileName):
#*************************************************************************
#Method : getEncodeStr
#In     : List containing tag details for music file and wave file name
#Purpose: Create string that will contain command line to encode music file
#Out    : String containing command line
#*************************************************************************

	# Put switches in list depending on format
	if ENC_FORMAT == 'OGG':
		commList = [' -a ', ' -l ', ' -t ', ' -d ', ' -N ', ' -G ']
		# Change this to path where oggenc is located if different 
		encStr = '/usr/bin/oggenc '+  wavFileName 
		musicFilename = ' -o ' + tagList[0] + '-' + tagList[6] + '.ogg'
	else:
		commList = [' --ta ', ' --tl ', ' --tt ', ' --ty ', ' --tn ', ' --tg ']
		# Change this to path where lame is located if different 
		encStr = '/usr/bin/lame '+  wavFileName	
		musicFilename = tagList[0] + '-' + tagList[6] + '.mp3'
	
	# Add switches and tags to string
	encStr += commList[0] + '"' + tagList[5] + '"'
	encStr += commList[1] + '"' + tagList[1] + '"'
	encStr += commList[2] + '"' + tagList[6] + '"'
	encStr += commList[3] + tagList[2]  
	encStr += commList[4] + tagList[0]  
	encStr += commList[5] + tagList[3]  
	encStr += ' -b ' + str(BITRATE) + ' ' + musicFilename
	return (encStr)

def getEncodeList(encString):
#******************************************************
#Method : getEncodeList
#In     : String containing tag details for music file
#Purpose: Extract all tag details into list
#Out    : List containing tage commands
#******************************************************

	encString = encString.replace('.wav', '')
	tagList = encString.split('-')
	return(tagList)


def encode():
#********************************************
#Method : transcode
#In     : none
#Purpose: Encode all files in current folder
#Out    : None
#********************************************
	

	# Setup vars used in main loop
	x =0
	file_list = glob.glob('*.wav')
	file_list.sort()
	len_list = len(file_list)
	# loop through list to encode	
	while x < len_list:
		fileName = file_list[x]
		encList = getEncodeList(fileName)
		encStr = getEncodeStr(encList, fileName)
		print("\nEncoding track " + encList[6]) 
		#print(encStr)
		os.system(encStr)
		x +=1
		

def main():
#*************************************************************************************
#Method : main
#In     : none
#Purpose: Loop through all sub folders in main folder and encode if wav files exist.
#Out    : None
#*************************************************************************************
		
	for root, dirs, files in os.walk(SOURCE_DIR, topdown=False):
		for name in dirs:
			os.chdir(os.path.join(root, name))
			encode()
				
if __name__ == "__main__":
    main()

``` 

The script can either encode to MP3 or OGG format. Amend the BITRATE and  
ENC_FORMAT variables to format and bit rate.

After saving the file type the following command at the prompt:

```

chmod +x encode.py

```

Use grip to rip the CD. To run the script just enter
```

./encode.py

```

The beauty of this script is that it can encode multiple CD's as long as the folders are in the source folder you have defined in script.

---

