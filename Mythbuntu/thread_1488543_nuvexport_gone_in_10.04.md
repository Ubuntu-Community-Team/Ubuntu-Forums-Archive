---
title: "nuvexport gone in 10.04?"
date: 2010-05-20
forum: Mythbuntu
---

### Post by linuxhippy on 2010-05-20
I upgraded mythbuntu 9.10 to 10.04 and noticed that some things don't work now.  One is that nuvexport is not installed and I cannot download it with synaptic (it's missing dependencies).  So, was nuvexport removed and more importantly, how do I now export an nuv file to an mpg file without the commercials in 10.04?

---

### Post by linuxhippy on 2010-05-21
I was able to transcode it to a high nuv recording by pressing M while watching the edited video in mythtv and choosing transcode>high.  It then puts a nice nuv file without commercials into the directory specified in archive settings (it's huge...1.8 GB for a 45 minute program).  This file can then be opened with VLC on another pc and I imagine I can use mencoder to convert the nuv file to an mpg.

The problem I see now is that the top 1 mm of my screen has some moving lines.  I was told that this is removed by TVs but monitors (like I am using) do not remove this.  I was able to have mythtv remove these lines while watching videos by offsetting the position of the screen...how can I remove this from a file?

---

### Post by linuxhippy on 2010-05-23
I have no idea where nuvexport went...it was flawed, though, so I'm thinking it is deprecated.  I did figure out how to use ffmpeg to take the transcoded nuv with no commercials and convert it to a widescreen ntsc dvd mpg file.  I cut off the top of the screen to delete the annoying lines there:

ffmpeg -i V-RedSky.nuv -croptop 4 -y -target ntsc-dvd -sameq -aspect 16:9 -async 1 RedSky.mpg

I then used dvdstyler to burn the mpg file to a dvd for a TV.  I noticed I can archive with devede since it has the option for making DivX dvds.

---

### Post by db260179 on 2010-05-24
> **linuxhippy said:**
> I upgraded mythbuntu 9.10 to 10.04 and noticed that some things don't work now.  One is that nuvexport is not installed and I cannot download it with synaptic (it's missing dependencies).  So, was nuvexport removed and more importantly, how do I now export an nuv file to an mpg file without the commercials in 10.04?

I think nuvexport was made redundant for MythtvExport in the Mythbuntu Control Centre?

---

### Post by linuxhippy on 2010-05-24
I'll look at that again-thanks!

---

### Post by Lepy on 2010-05-27
You can also try mythnuv2mkv: [http://web.aanet.com.au/~auric/?q=node/6](http://web.aanet.com.au/~auric/?q=node/6) & [http://www.mythtv.org/wiki/Mythnuv2mkv](http://www.mythtv.org/wiki/Mythnuv2mkv)

If your recordings don't specifically need to be saved as mpgs, this script can replace or export your recordings to a folder all while honouring your commercial cut list and converting to a space saving format (xvid or x264 in avi, mp4 or mkv).

You must make a few minor changes to the script and set up user jobs, but it works very well. The only problem I have experienced is some long digital recordings going out of sync, but ymmv depending on your source signal.

---

### Post by laffinet on 2010-05-27
+1

I use mythnuv2mk all the time to convert my recordings to space saving mkv files. I have it set up as a user job to be run from inside mythtv. Very convenient.

You can also set it up to replace the original recording. That way the recording still shows up in the recordings menu, together with all the info, but the file size is a lot smaller.

---

