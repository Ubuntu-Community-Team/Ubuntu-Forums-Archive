---
title: "Disney encrypted DVDs and Linux"
date: 2011-11-22
forum: Multimedia Software
---

### Post by bruno9779 on 2011-11-22
I have recently bought Cars 2 dvd for my little kid. He loved the first installment of the series, so I bought the second one hoping to give him a nice surprise.

I don't own any other recent Disney DVD, so I wasn't familiar with the issues this presents.

At the beginning it didn't work at all, so I installe CCS and libdvdread as suggested by several tutorials.
After this the DVD started, but VLC kept freezing (every 30-300 seconds) and smplayer would simply skip several frames (also every 30-300 secs).

I have tries increasing the cache and many many other fixes, to no avail.

Quite pi**ed off already I have decide to try and rip the disk, to see it somehow: dvd:rip and acidrip didn't recognize the disk and handbrake isn't available for oneiric. Previous versions of Handbrake did not work either.

After several frustrating attempts, and a few hours googling around, someone suggested trying to build handbrake from SVN.
Unity doesn't go well with it and I can only start it from CLI, but finally I could rip the title. It even found out which one of the 99 bogus titles is the real one automatically.

My son watched the movie and loved it as expected, just, did it have to be this hard?

---

### Post by wolfen69 on 2011-11-22
Handbrake is available for 11.10
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install handbrake-gtk ffmpeg
```

---

### Post by SeijiSensei on 2011-11-22
Don't expect Handbrake to solve your problem.  There is a class of DVDs that use a [method of copy protection]("http://en.wikipedia.org/wiki/ARccOS") that Linux cannot handle correctly.  I'm almost positive Disney uses that method.

---

### Post by lisati on 2011-11-22
I recall seeing similar questions arise in the past. Here are some related threads:

[http://ubuntuforums.org/showthread.php?t=1807037](http://ubuntuforums.org/showthread.php?t=1807037)
[http://ubuntuforums.org/showthread.php?t=1687807](http://ubuntuforums.org/showthread.php?t=1687807)
[http://ubuntuforums.org/showthread.php?t=1264978](http://ubuntuforums.org/showthread.php?t=1264978)


[http://ubuntuforums.org/showthread.php?t=1809745](http://ubuntuforums.org/showthread.php?t=1809745)

---

### Post by jawilljr on 2011-11-22
Try [MakeMKV](http://www.makemkv.com/forum2/viewforum.php?f=3&sid=1aa285a6b81bf2c306bf992a5ac48c88).

So far I have yet to not be able to rip a copy protected DVD.

Jerry.

---

### Post by bruno9779 on 2011-11-22
@ wolfen69 : The ppa I found on their website is ppa:stebbins/handbrake-releases. And Oneiric isn't included

@ SeijiSensei : Handbrake is the only ripping software I have found that can read the DVD's TOC. Apparently this is because it uses VLC to decode the DVD.
Now I have a big lossless .mkv of the movie with dual audio and subs. It sounds as a solution to me.

@ jawilljr : I am checking that out. Thanks

---

### Post by wolfen69 on 2011-11-22
> **bruno9779 said:**
> @ wolfen69 : The ppa I found on their website is ppa:stebbins/handbrake-releases. And Oneiric isn't included



The info I gave you will work, as I'm using 11.10 and handbrake. ;) I didn't get the ppa from their website, but rather at Launchpad. I can assure you it works.

---

### Post by dniMretsaM on 2011-11-22
> **SeijiSensei said:**
> Don't expect Handbrake to solve your problem.  There is a class of DVDs that use a [method of copy protection]("http://en.wikipedia.org/wiki/ARccOS") that Linux cannot handle correctly.  I'm almost positive Disney uses that method.

From the Wiki:
>  [ARccOS] is also naturally overcome by using [ddrescue]("http://en.wikipedia.org/wiki/Ddrescue"), a linux utility designed to copy images with errors.

This should work (though I can't confirm it):
```
ddrescue -n -b <block-size> /dev/dvd <dvd-name>.iso
```

The <block-size> for most DVD's is 2048.

---

### Post by mc4man on 2011-11-23
The biggest issue with **Playback** of these discs, (which it sounds what you wish to do), is that the players can't find the real movie title number & the 'normal' navigation to it messes them up.

Vlc should be able to play the movie if you give it the proper title #.

If you have a standalone hardware dvd player start the movie, (the actual movie), then most players will show you the title # in one of the menus, osd, whatever.

Then use vlc either from command line or gui

For gui open vlc > Media > Open Disc.
Click on "No dvd Menus" & in the Starting Position section enter the title number & chapter 1 (usually chapter # could also be left at 0 

Then click on play

For command line while in the above screen click on Show more options. THe command is right there, just copy & paste into terminal, Ex. 
```
vlc dvdsimple:///dev/sr0@18:1
```

Command means 'no menus'(dvdsimple://), 'device' (/dev/sr0), @ (title:chapter

A quick glance around suggests title 15 may be the main movie title for some regions
**Edit**: - decided to pick up a copy - the main movie title in R1 is 18


ddresue & dvdisaster are both good for dumping an encrypted, structure protected .iso that will play back on the pc **just like the orig. disk.**

Further edit - The only player i have on 11.10 that will play this title & use all the menus is totem-xine which was discontinued some time ago. But as edited above & in screen vlc will play the main movie. Note that the first screen shows title 15, the actual title is 18

---

### Post by JohnAStebbins on 2011-11-23
> **SeijiSensei said:**
> Don't expect Handbrake to solve your problem.  There is a class of DVDs that use a [method of copy protection]("http://en.wikipedia.org/wiki/ARccOS") that Linux cannot handle correctly.  I'm almost positive Disney uses that method.

HandBrake handles ARccOS just fine if you are using the dvdnav option (which is enabled by default).  Cars 2 is a special case where they corrupted some of the directory information and crashed libdvdread.  The HandBrake snapshots have a fix for this (which also affects Transformers 3).

Any linux software that uses libdvdnav will handle most ARccOS discs.  VLC is pretty good for this since it also shows you the DVD menus.

---

### Post by rickyrockrat on 2011-11-23
Gents,
There are various methods to rip all DVDs encountered so far. I've written a script around vobcopy, vlc, mplayer, ddrescue, isoinfo, and dvdbackup, and soon handbrake. I have not found a single movie that cannot be ripped on Linux. Some of them take more patience than others.

If dvdbackup will not reliably give you the main title, you can use HandbrakeCLI. Sometimes you have to use VLC to play the movie, then find out what title it's using.  These are all a PITA, and have changed me from a staunch anti-piracy advocate to a staunch piracy, anti RIAA/MPAA advocate.

There's a fix for libdvdread here:
[http://ubuntuforums.org/showthread.php?t=1844512](http://ubuntuforums.org/showthread.php?t=1844512)
Though I did find one movie it broke, and it actually ripped with the old version. I hate this crap. I just want to watch movies I legally bought or rented.

Here's some other tidbits for ripping DVDs - these come from my working
scripts:
```

dvd_dev=/dev/sr0
#DVD info
HandbrakeCLI -i /dev/sr0 -t 0 > dvdscan.txt 2>&1
vobcopy -I
movie_name=$(isoinfo -d -i "$1"|grep -i "volume id"|sed 's!.* \(.*\)!\1!')
main_title=$(dvdbackup -i "$1" -I 2>>$log|grep "Title set"|grep "main feature is"|tr -d '[:alpha:][:punct:][:space:]')

mpg_name="$movie_name.mpg"

#byte copy, no decrypting, use to save a bit copy
ddrescue -b 2048 "$dvd_dev" "$outf"
# Rip title, dout is a directory
dvdbackup  -T "$title" -i "$dvd_dev" -o "$dout" -n "$mpg_name"
#Auto figure main title using dvdbackup
dvdbackup -F -i "$dvd_dev" -o "$dout" -n "$mpg_name"
# Mirror DVD while decrypting dout is a common directory, uni_base is a directory to put the VIDEO_TS in
dvdbackup -M -i "$dvd_dev" -o "$dout" -n "$uni_base
# Decrypt title with mplayer
mplayer dvd://${title} -dvd-device "$dvd_dev" -dumpstream -dumpfile "$mpg_name"
# Decrypt title with vlc
vlc "dvdsimple://${dvd_dev}@${title}" --intf dummy --sout "#standard{access=file,mux=ts,dst=$mpg_name}" vlc://quit

#find the (often FAKE size) of the data on the DVD
# if filesum is over 8-10G, you know you have a purposely
# broken DVD file system. They spoofed the files, and most of them
# point to the same data or nowhere at all. You have to find the right
# title and rip it- don't bother mirroring a DVD like this. Waste of 
# space and time.
get_reported_filesum (){
while read d a b c sz garbage; do
 let filesum=filesum+sz
done << EOF
$(isoinfo -l -i "$1")
EOF
let filesum=filesum/1000000
}


```
On DVDs with 99 titles, this will be a big list, but Handbrake often correctly identifies the main title, for example on Captain America, it's title 25, and successfully ripped with mplayer. I tried 3 and 93, but they would go to like 90% of the movie, then stop. A new way to irritate us, I suppose.  Cars 2 is title 18, and appears to rip just fine using mplayer.

How very interesting. Mplayer will rip the movie, and VLC will navigate & play the correct title most of the time, but it often rips with some encoding still there.

If there's enough interest, I may post my script(s). They also wrapper dvdauthor and mkisofs, so DVDs can be created from the ripped results.

Here's a bit on the libdvdread patch, and how to rip Thor:
[http://ubuntuforums.org/showthread.php?t=1844512](http://ubuntuforums.org/showthread.php?t=1844512)

There are two patches now for libdvdread, and both the libdvdread must be patched, and the mplayer libdvdread.  It's a pain they use different libraries!
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=649790](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=649790)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641881](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641881)
The same bug reports have been submitted for Ubuntu as well.


Cheers!
I'm seriously thinking of making a sourceforge project with my scripts, since this is a very common issue.

---

### Post by underquark on 2011-11-23
Just as I was thinking of streaming videos but couldn't play back my (genuine) Pirates....Tides DVD, along comes a NAS from a friend and this thread to jog my memory.  Hats off to Handbrake, yet again, for making a 1.1Gb file that plays back well.  VLC had been showing pixellated garbage off the original DVD, K9copy was barfing with segmentation errors and K3B offered to make me a 23-hour video.

"Some of them take more patience than others." - Definitely.

---

