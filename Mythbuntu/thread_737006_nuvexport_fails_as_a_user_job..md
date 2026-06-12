---
title: "nuvexport fails as a user job."
date: 2008-03-27
forum: Mythbuntu
---

### Post by mickfromperth on 2008-03-27
Howdy All.

I have been struggling with HDTV recording over DVB.  I don't have the harddrive requirements.  I only have an 80G harddrive spare for experimenting with MythTV.

So; what I currently do is use the build in trascode system to trascode these HD recordings intosomething closer to SD recordings.  But the build in transcoder will only store these files in a nuv container.

Also..  I don't use mythtv to watch recordings; I use my one and only UPNP frontend: The PS3.

This is where my struggle begins. Now I know people have found streaming ts streams an issue because of buggy code on the PS3.  But my TS stream is long gone when I transcoded into nuv (Isn't it?).

So what I tried to do was to not use the inbuild transcode; but use nuvexport instead.  There is an excelant howto on this in the howto section of the ubuntu forum.  Linked below:
[http://ubuntuforums.org/showthread.php?t=346778](http://ubuntuforums.org/showthread.php?t=346778)

Not quite complete as per the terminal emulation issues but it gets the job done.

Except not for me..  nuvexport for me will not authenticate to the database [when run as a user job only].  When I run from the command line it works fine.  I've posted on the above HOWTO some questions but so far no answers..  

Which leads me to believe.. maybe there's a better way??  Maybe people have moved off of nuv-export and into some other wonderful place??

Currently I'm streaming my media files via FUPPES UPNP server which will transcode just about anything on the fly..  However; it seems unable to read nuv files.  So I'm in need of a solution which will will give me either mpeg, avi, or mp4 contained divx.

I would really love it if this solution would also delete the original files once it's done.

Can some of you please advise me on what is the best way to achieve this??

Cheers,
Mick

---

### Post by foxbuntu on 2008-03-28
Currently, AFAIK, people are using MythExport (the new nuvexport) in Myth 0.21 and with the latest 2.20 code from the PS3 UPNP is supposed to be fixed. I also am aware that there is a patch for FUPPES coming soon that sould resolve that issue as well...so I would say dig around for help on MythExport + PS3 for now and the FUPPES update should be shortly behind.

---

### Post by Anubis on 2008-04-26
Mythexport is NOT the new nuvexport.

[http://tacomafia.net:8080/blog/2006/mythexport/#comment-35](http://tacomafia.net:8080/blog/2006/mythexport/#comment-35)

The two scripts do completely different things.

This script cuts commercials and transcodes. The author calls his mythexport unoriginally though. I have yet to get anything nuvexport to run from jobline. Only nuvexport runs from command line, and then does not even output the file in a readable format like it claims to. Why is this package in the repos if there is absolutely NO support for it?:confused:

[My ~.nuvexportrc]("http://pastebin.com/f2182b36d")

nuvexport-xvid --ffmpeg --quantisation 4  --a_bitrate 128 --v_bitrate 4000 --nice 10 --infile="%FILE%"

nuvexport --ffmpeg --infile="%FILE%" --path=/home/anubis/store/mythtv/video/nuvexport --height=640 --width=480 --mode=xvid --deinterlace --nonoise_reduction --nice=19

---

