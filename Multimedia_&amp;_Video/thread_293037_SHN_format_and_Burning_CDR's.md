---
title: "SHN format and Burning CDR's"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by AndrewB on 2006-11-04
Please help an aged Dead-head.  I have been able to get shn's to play on both XMMS and gstreamer front ends. However, what I'd like to do is burn some shows onto CDR. I have using gnomebaker for data/audio disks.

I appreciate any and all help.

Sincerely,
Andrew

---

### Post by AndrewB on 2006-11-09
Due to overwhelming interest, here is what I found....shn2make. I don't have it running yet, and could still use some help. As I'm by no means beyond Ubuntu beginer level.  Have a look:> AME
       shn2make - A tool for working with sets of shn and flac audio files

SYNOPSIS
       shn2make [ options ]

DESCRIPTION
       shn2make  works  with sets of shn or flac audio files and the make pro-
       gram to automate the process of burning shn archive CD-R's,  audio  CD-
       R's and the encoding of lossy mp3 and ogg-vorbis files.

       shn  and  flac are lossless audio compression formats. shn and flac are
       commonly used for  distribution  of  high-quality  live  recordings  of
       "trade friendly" bands. You will find many via etree.org , or in USENET
       groups like alt.binaries.gdead.

       shn and flac file sets are typically distributed with a  .nfo  or  .txt
       file which contains the set list and other information.

      ~~~~~~~~~
version 2.14                      10 Oct 2005                      shn2make(1)


---

### Post by christhemonkey on 2006-11-09
That program soudns like it does what you want.

To get it to work download it (i cant seem to connect to their ftp server to get it so im not sure how it is distributed, please let us know what files there are to install) and then type:

```
cd /directory/where/y/our/shn/files/are 
```
To change to where the files are.

```
shn2make 
```
To generate the makefile of what you want.

```
make shnarchive1 
```
TO burn to cd (make sure there is a blank cd in the drive!

---

### Post by christhemonkey on 2006-11-09
Just noticed this project hasnt been updated in the last 4 years.

Maybe there is another solution.


Shntool which is in the repositories looks like it will do the job nicely.

```
sudo apt-get install shntool 
```

Then read this page:
[http://etree.org/shnutils/shntool/](http://etree.org/shnutils/shntool/)

And folow the instructions for getting shn support.

---

### Post by AndrewB on 2006-11-09
> ERROR: $no CDR_DEVICE defined in /home/andrew1165/.shn2makerc and no CDR_DEVICE environment variable


 I'm making slow progress. > cdrecord -scanbus is not returning any usable info to fill in the rc file> .shn2makerc

Why does this have to be so F'in hard in Linux.](*,)  In windows I'd have been done  a week ago, and had fresh music to listen to on my trip :(

I'm out of time. Will try shntools when I get back in a week.

---

### Post by teloschistes on 2006-11-12
I'm a beginner at all this, but the following works for me....

Add the following line to /etc/apt/sources.list

deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

Then,
```
# apt-get update
# apt-get install shorten
```
The "#" just means as root, I just can't get used to sudo, but 6/one half-dozen....
Might as well have flac capabilities too...
```
# apt-get install flac
```
Save the following in a text file, somewhere in your path, like /usr/local/bin
```
#!/bin/bash
#this script will erase your shn/flac files -- archive first!

echo -e "\E[34m\n::shn/flac -> wav::\n"
echo -e "\E[0m"

if ls *shn &>/dev/null ; then
for shnfile in *.shn ; do
echo -e '\E[34m\n::decoding '$shnfile'::\n'; echo -e '\E[0m'
shorten -x "$shnfile" "$shnfile".wav && rm -f "$shnfile"
done
fi

if ls *flac &>/dev/null ; then
for flacfile in *.flac ; do
echo -e '\E[34m\n::decoding '$flacfile'::'; echo -e '\E[0m'
flac -d "$flacfile" && rm -f "$flacfile"
done
fi

if ls *shn &>/dev/null || ls *flac &>/dev/null ; then
echo -e '\E[34m\n::nulla per nota commutata sunt::' ; echo -e '\E[0m'
elif ls *wav &>/dev/null; then
echo -e '\E[34m\n::omnia per nota commutata sunt::' ; echo -e '\E[0m'
else echo -e '\E[34m\n::nulla per nota commutata sunt::' ; echo -e '\E[0m'
fi

exit

```
Name it something like shn2wav and make it executable.
```
# chmod +x shn2wav
```
Navigate to the directory with your shn files and...
```
$ shn2wav
```
Then you will (hopefully) have a directory full of wav files, which you can then input into the burning app of your choice.

Hope this helps...

---

### Post by AndrewB on 2006-11-17
I guess I've made some progress, thanks teloschistes. 


update: I sucsessfully transcoded some shn's today.

Many, Many Thanks:)
\


Note:

I was able to burn the wav files to a data disk in Gnomebaker. Am still having trouble getting gnomebaker to burn the files as an audio disk,> The plugin to handle a file of type audio/x-wav is not installed. So still digging for the last puzzle piece.

---

### Post by AndrewB on 2006-11-17
The > gstreamer0.8-pluginsmeta-package seems to have taken care of my wav file \ audio disk needs. 

I believe this is done. Case closed, teloschistes, christhemonkey, either of you ever in my neck of the woods, coffee's on me:twisted:

---

### Post by christhemonkey on 2006-11-18
Connecticut is a bit of a trek from here but thanks il hold you to that! :D

---

