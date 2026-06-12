---
title: "Devede and .srt"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by topic58 on 2007-07-29
I use Ubuntu 6.10 and Devede to make DVD. Now I want to put a .srt into the DVD. My Devede in 6.10 just have the option to add a commandline to mencoder. But I don't know what to write. Someone? I got an .avi with .srt and want to make a Video DVD (first option in Devede) with sub.

---

### Post by topic58 on 2007-07-29
OR - is there a simple way to burn the .srt in to the .avi before using Devede?

---

### Post by topic58 on 2007-07-29
Okay.. New version of Devede, 3.somthing has it built in to burn .srt into the DVD. BUT Devede use mencoder. SO, someone clever out there must know how to write the code to make this work if it's built in in Devede. Right? Someone who is good at using mencoder in the terminal.

---

### Post by topic58 on 2007-07-31
Found this when looking for mencoder and .srt.

Assuming your subtitles are in a file mymovie.srt, and your movie in mymovie.avi, now run: mencoder -sub mymovie.srt -subpos 85 -vf expand=640:384 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800:vhq -oac copy -o mymovie2.avi mymovie.avi 

Tried it in terminal and it seemed to work well. You may change the vbitrate though. There is a calc for vbitrate on videohelp.com. I changed vbitrate to 900. Higher vbitrate = more MB.

---

### Post by izhitzza on 2007-07-31
If you have an avi, you probably will need to convert it first to MPEG2, using either (a) mencoder, (b) transcode, or (c) ffmpeg. I choose to use ffmpeg like so:

$ ffmpeg -i movie.avi -pass 1 -target ntsc-dvd -aspect 16:9 movie.mpg

Check out a gentoo forum thread: [http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode)

Next, you can add .srt subtitles to your movie using spumux (comes with dvdauthor), you will need to create a small XML configuration file, try something like this:

<subpictures>
        <stream>
                <textsub filename="subtitles.srt"
                        font="arial.ttf"
                        characterset="UTF-8"
                        horizontal-alignment="left"
                        vertical-alignment="bottom"
                        left-margin="60"
                        bottom-margin="80"
                        fontsize="18.0"
                />
        </stream>
</subpictures>

Only make sure you have a font file arial.ttf in your home directory: ~/.spumux, if you don't you can just copy one from your /usr/share/fonts/truetype.

If everything went Ok, you should have a good movie.mpg file with the subtitles, now you can author that like this:

$ dvdauthor -f movie.mpg -o dvd

This will create a dvd-structure that you can then create an ISO image from:

$ mkisofs -dvd-video -V TITLE_NAME -o dvd.iso dvd

And then just burn dvd.iso to a DVD disc. For more on this read here: [http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)

Good luck,
Alex.

---

### Post by xpan on 2007-08-26
when giving:

> dvdauthor -f movie.mpg -o dvd

I got this error:

DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt iconv freetype fribidi
Send bugs to <dvdauthor-users@lists.sourceforge.net>

ERR:  Must first specify -t, -m, or -x.

I give: 

> dvdauthor -t movie.mpg -o dvd

and it seems to work, creating a dvd/ folder with contents a VIDEO_TS and an AUDIO_TS subfolder. AUDIO_TS is empty, though

then I give:

> mkisofs -dvd-video -V TITLE_NAME -o dvd.iso dvd

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for 'dvd/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents


any ideas what am I doing wrong?

PS: VIDEO_TS.IFO exists but with a different file name: VTS_01_0.IFO

PS2: What should the name of the xml file be?

---

