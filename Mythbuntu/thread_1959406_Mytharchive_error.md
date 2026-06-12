---
title: "Mytharchive error"
date: 2012-04-15
forum: Mythbuntu
---

### Post by Leechpool on 2012-04-15
Hi,
I'm using mythbuntu 11.10
I installed mytharchive and tried to create a DVD from a recording.
It failed with the error
"cannot write mode I as jpeg"
log implied error was from line 425 of /usr/lib/python/dist-packages/PIL/jpegimageplugin.py
Can anyone advise as to what is going wrong.
If I try to create the DVD using the simple autostart DVD with no menu etc it seems to work ok but would like to create with menus etc.
I've tried googling but am getting nowhere and I know little about python....
I suspect the error occurs when an attempt is made to extract a frame to use as a menu thumbnail. Could the issue be that the script did not anticipate the codec/format used in the UK digital terrestiral trasnmissions DVB-T?
Thanks
:p

---

### Post by BicyclerBoy on 2012-04-21
I've made DVDs from similar DVB-T recordings..but not using 11.10..

I'd guess there is a missing dependency for package "libmng1".

The python file in your error log has a different path(s) on my PC..
/usr/lib/python2.6/...
& /usr/lib/python2.7/...

---

### Post by rmcd on 2012-05-21
Using 12.04 and myth 0.25 I have the same error as @BicyclerBoy, but there also seems to be a permissions problem. 

```

Truncated text = 
chmod: changing permissions of `/var/lib/mytharchive/temp/': Operation not permitted
------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5182, in main
    processJob(job)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 4891, in processJob
    createMenu(format, dpi, files.length)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 3552, in createMenu
    bgimage.save(os.path.join(getTempPath(),"background-%s.jpg" % page),"JPEG", quality=99)
  File "/usr/lib/python2.7/dist-packages/PIL/Image.py", line 1439, in save
    save_handler(self, fp, filename)
  File "/usr/lib/python2.7/dist-packages/PIL/JpegImagePlugin.py", line 425, in _save
    raise IOError("cannot write mode %s as JPEG" % im.mode)
IOError: cannot write mode I as JPEG
------------------------------------------------------------

```

---

### Post by klc5555 on 2012-05-21
Recordings files are usually best stored under /var/lib/mythtv/ of course, but mytharchive itself is mostly a front-end activity initiated by the main user account, and so I found I always had permission problems with mytharchive unless I put mytharchive's temp working directory under the main user's home directory, rather than under /var/lib/mythtv/

That said, in my own experience mytharchive has just not worked very well when it has worked at all since around Mythtv 0.20 or so. So consequently now, on the rare occasion when I want to make a DVD of a show or group of shows, I tend just to use nuvexport to export the recording(s) to a working directory and then use a 3rd-party tool like DeVeDe to transcode and prepare the actual .iso file for burning. Fewer synch issues, fewer coasters, generally a smoother experience.

---

### Post by rmcd on 2012-05-21
Thanks for the advice. But I can't find nuvexport. I recall using it several years ago. Is it still part of myth? 

And how do I change the mytharchive working directory? I can't find the entry among the myth setup menus.

Thanks.

---

### Post by klc5555 on 2012-05-21
nuvexport has been back in Mythtv since about 0.23.

Mytharchive is a frontend utility. Its params are usually set from the frontend setup; see here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Videos_Settings](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Videos_Settings)  under "MythArchive Settings"

---

### Post by rmcd on 2012-05-21
Thank you! I've learned a few things.

1. DeVeDe is a terrific program. It successfully created a dvd (pretty rudimentary) from my mpg file. 

2. nuvexport may be in myth 0.25, but I can't find it. It doesn't show with locate, it doesn't run from the command line, I simply can't find it. I have installed every myth-related package I could find. 

3. You're correct about the archive settings. I thought I had gone through all the settings options, but I must have just missed the archive settings earlier. I'm experimenting now with putting the temp directory under my home directory. It would be nice if mytharchive worked.

---

### Post by rmcd on 2012-05-21
Mytharchive still does not work when I move the temp directory, but now there is no permissions error, only the "cannot write mode I" error:

```
2012-05-21 22:29:33 Music is silence.ac3, length is 15 seconds
2012-05-21 22:29:33 Creating DVD menus
2012-05-21 22:29:33 Menu page 1
2012-05-21 22:29:33 Creating Preview Video
2012-05-21 22:29:33 Added image /home/rmcd/temp/mythtemp/work/1/title.jpg
2012-05-21 22:29:33 ------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 5182, in main
    processJob(job)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 4891, in processJob
    createMenu(format, dpi, files.length)
  File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 3552, in createMenu
    bgimage.save(os.path.join(getTempPath(),"background-%s.jpg" % page),"JPEG", quality=99)
  File "/usr/lib/python2.7/dist-packages/PIL/Image.py", line 1439, in save
    save_handler(self, fp, filename)
  File "/usr/lib/python2.7/dist-packages/PIL/JpegImagePlugin.py", line 425, in _save
    raise IOError("cannot write mode %s as JPEG" % im.mode)
IOError: cannot write mode I as JPEG
```

---

### Post by klc5555 on 2012-05-22
I'm still back on (mostly) 0.24, but traditionally nuvexport is found under Mythextras, from where it may be installed:

[http://www.mythtv.org/wiki/Release_Notes_-_0.25#Mythextras](http://www.mythtv.org/wiki/Release_Notes_-_0.25#Mythextras)

As far as mytharchive goes, I have no idea here. You may have come across a mytharchive/python bug that needs to be reported. There are some open tickets on mytharchive, but none seems to correspond with the python jpeg plugin problem described in the current thread. 

With DeVeDe, I've noticed that it tends to calculate and produce an iso that's way smaller than what could fit comfortably on the dvd medium (4 gig or 8 gig) that I'm using. Accordingly I never use the "fit on disk" option, I ignore DeVeDe's calculation of what percentage of the disk will be full, and I max out the bitrate for each recording from the default 5000 to 8500 (in the "advanced settings" for the recording) and then burn the resulting iso to whichever size medium the iso file's size will fit on, 4 or 8 gig. 

This seems to significantly improve the dvd quality from HD recordings, where DeVeDe at its defaults tends to drop too many frames, leaving fast-motion scenes somewhat herky-jerky.  In the rare occasions when the resulting iso won't fit the desired medium, I'll go back, dial down the bitrate a tad, and process the recording again.

But your mileage may vary.

---

### Post by nathank2 on 2012-08-05
I have the same prob with mytharchive using 0.25, but I switched to the Compact theme and it worked.

---

