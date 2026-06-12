---
title: "2 problems with Mytharchive (DVD)"
date: 2010-01-21
forum: Mythbuntu
---

### Post by ubnewbie2 on 2010-01-21
I just tried to burn my first DVD using my new mythbuntu 9:10 install.

It got all the way through until it actually tried to burn the result - and this failed (the screen showed no obvious reason why).  However, I was able to pick up the files from the mytharchive working directory and burn them on another machine using K3B.  The resulting DVD works.

So the two problems to solve are

1.  Why did it fail to burn these files to the DVD I left in the DVD drive?
2.  The sound is out of synch when I play the programs I recorded and chose to archive to the DVD.

---

### Post by klc5555 on 2010-01-21
There are lots and lots of seemingly intractable problems with mytharchive, and have been since about the transition from mythtv 0.20.2 to 0.21 two years ago.

To get an idea about why the burn end of things failed, take a look at the end of the mythburn.log which should have been left (along with the progress.log) in the working directories where mytharchive was processing the archive. For archives which blow up right near the burn stage, a frequent problem is the utility miscalculating the amount of free space required on the DVD, and then terminating. But it could be other things.

As far as audio sync goes, this has been a constant frustration with the archiving of DVB recordings with mytharchive since 0.21 came out. It doesn't afflict the archiving of analog recordings nearly as much, and so I'd personally recommend using mytharchive only for the archiving of analog recordings. For archiving DVB recordings, I rely mostly on DeVeDe, which does not suffer from audio sync problems. For the very rare recording that causes DeVeDe trouble, I use nuvexport --transcode at a high quality setting to produce a high-quality temporary .avi of the recording I want to archive as an intermediate stage, then I feed this .avi into DeVeDe.

Anyway, that's what I do. Other people will have different solutions. 

Cheers! :)

---

### Post by ubnewbie2 on 2010-01-21
Thanks for the advice.  yes, these are DVB recordings.  I will try DeVeDe, but from first looks at it's web page, it is a standalone app.  Does that mean it can't read the mythtv database and find the correct recording by name instead of me having to translate the recording I want to the name mythtv actually stores it as??

---

### Post by klc5555 on 2010-01-22
> **ubnewbie2 said:**
> Thanks for the advice.  yes, these are DVB recordings.  I will try DeVeDe, but from first looks at it's web page, it is a standalone app.  Does that mean it can't read the mythtv database and find the correct recording by name instead of me having to translate the recording I want to the name mythtv actually stores it as??

That's right: it's a standalone and does not read mythconverg information.

But what I do to keep the archiving with DeVeDe fairly simple is first to set up the working directory I want to for archiving purposes and then use the mythtv utility "nuvexport" with the option to "export .nuv and .sql" to find the shows for me that I want to archive and "export" them (that is, copy the .mpg files) into the working directory. A copy of the file for each show to be archived ends up in the working directory, each episode its own labelled folder with all necessary show information. Makes it easy to dump the correct files for the correct episodes in the correct order onto the DVD that you set up to create with DeVeDe. 

When DeVeDe has cranked out the *.iso file, use your favorite burner (like most folks I use k3b) to burn it to disk.


Admittedly, a smoothly and correctly working mytharchive utility would be a preferable solution for DVB archiving. But I don't believe we're ever likely to see that. In the meantime there are lots of digital recordings to be archived and one soon gets tired of the expense of pitching disks because the audio sync is all over the place.

---

### Post by ubnewbie2 on 2010-01-22
> **klc5555 said:**
> That's right: it's a standalone and does not read mythconverg information.

But what I do to keep the archiving with DeVeDe fairly simple is first to set up the working directory I want to for archiving purposes and then use the mythtv utility "nuvexport" with the option to "export .nuv and .sql" to find the shows for me that I want to archive and "export" them (that is, copy the .mpg files) into the working directory. A copy of the file for each show to be archived ends up in the working directory, each episode its own labelled folder with all necessary show information. Makes it easy to dump the correct files for the correct episodes in the correct order onto the DVD that you set up to create with DeVeDe. 

When DeVeDe has cranked out the *.iso file, use your favorite burner (like most folks I use k3b) to burn it to disk.


Admittedly, a smoothly and correctly working mytharchive utility would be a preferable solution for DVB archiving. But I don't believe we're ever likely to see that. In the meantime there are lots of digital recordings to be archived and one soon gets tired of the expense of pitching disks because the audio sync is all over the place.

I will try exactly your solution - thanks.  Sad about mytharchive though.

---

### Post by DrCrispPacket on 2010-04-10
I am having problems in creating a DVD using stored videos (either from my home video recorder or from other sources such as BBC iPlayer). MythArchive works OK using TV recordings captured with my DVB card; in the past I have been able to write DVDs with MythArchive in Jaunty/Myth0.21, but since upgrading to Karmic/Myth0.22 I have been experiencing problems with stored videos.

When processing videos, MythArchive performs all the transcoding steps etc: ffmpeg and mythreplex proceed OK. It seems to fail in the part where it tries to generate a Menu, and returns the following code:

> 
2010-04-10 19:15:01 *************************************************************
2010-04-10 19:15:01 Processing video 1: 'Holidays/VeniceChoir.MP4'
2010-04-10 19:15:01 *************************************************************
2010-04-10 19:15:01 File type is 'mov,mp4,m4a,3gp,3g2,mj2'
2010-04-10 19:15:01 Video codec is 'h264'
2010-04-10 19:15:01 Preferred audio languages eng and eng
2010-04-10 19:15:01 Video id: 0x1, Audio1: [1] 0x2 (LIBFAAD, eng), Audio2: [-1] - 0x-1 (N/A, N/A)
2010-04-10 19:15:01 Aspect ratio is 4:3
2010-04-10 19:15:01 Re-encoding audio and video
2010-04-10 19:15:01 Using encoder profiles from /usr/share/mythtv/mytharchive/encoder_profiles/ffmpeg_dvd_pal.xml
2010-04-10 19:15:01 Encoding profile (SP) found
2010-04-10 19:15:01 ffmpeg -v 1 -i "/var/lib/mythtv/videos/Holidays/VeniceChoir.MP4" -r pal -target dvd -b 4771k -s 720x576 -acodec ac3 -ab 192k -ac 2 -copyts -aspect 4:3 "/var/lib/mythtv/videos/temp/work/1/newfile2.mpg" -map 0:0 -map 0:1 
2010-04-10 19:31:10 Preferred audio languages eng and eng
2010-04-10 19:31:10 Video id: 0x1e0, Audio1: [1] 0x80 (AC3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
2010-04-10 19:31:10 Splitting MPEG stream into audio and video parts
2010-04-10 19:31:10 Running: mythreplex --demux --fix_sync -o /var/lib/mythtv/videos/temp/work/1/stream -v 224 -c 128 "/var/lib/mythtv/videos/temp/work/1/newfile2.mpg"
2010-04-10 19:32:41 Audio is already in ac3 format
2010-04-10 19:32:41 Extracting thumbnail image from /var/lib/mythtv/videos/temp/work/1/stream.mv2 at position 10
2010-04-10 19:32:41 Destination file /var/lib/mythtv/videos/temp/work/1/title.jpg
2010-04-10 19:32:44 *************************************************************
2010-04-10 19:32:44 Finished processing 'Holidays/VeniceChoir.MP4'
2010-04-10 19:32:44 *************************************************************
2010-04-10 19:32:44 Menu items per page 4
2010-04-10 19:32:44 Background image file is /usr/share/mythtv/mytharchive/themes/Black/Black-Background.png
2010-04-10 19:32:44 Music is silence.ac3, length is 15 seconds
2010-04-10 19:32:44 Creating DVD menus
2010-04-10 19:32:44 Menu page 1
2010-04-10 19:32:44 Creating Preview Video
2010-04-10 19:32:44 ------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5434, in main
    processJob(job)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5153, in processJob
    createMenu(format, dpi, files.length)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 3781, in createMenu
    spumuxdom, spunode, numberofitems, 0,"")
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 3518, in drawThemeItem
    chapternumber, chapterlist)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 935, in expandItemText
    if getText( infoDOM.getElementsByTagName("coverfile")[0]) =="":
IndexError: list index out of range
2010-04-10 19:32:44 ------------------------------------------------------------

Can anyone suggest what is going on and how I might solve it? I thought the 'list index out of range' might have been an effect of having only one recording, with some sort of N-1 error, but the same problem occurs when I try to build a DVD with several files on it.

Thanks for any help.

Crisp Packet

---

### Post by DrCrispPacket on 2010-05-07
I find that burning video files to DVD works in MythArchive if I use the 'Add Files' option instead of the 'Add Videos'.  But why doesn't the other method work?

Crisp Packet

---

