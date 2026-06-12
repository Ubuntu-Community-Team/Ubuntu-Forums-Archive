---
title: "Help burning CDs (Brasero, XFburn)"
date: 2013-01-05
forum: Multimedia Software
---

### Post by Ken Kaniff on 2013-01-05
Hi,

I'm running a fresh installation of Xubuntu 12.04 LTS. My problem is that I'm unable to burn CDs. 

When trying to use Brasero I get the error below:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize Output set (AUDIO) image = /tmp/brasero_tmp_YJMDQW.cdr
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home--------.flac
BraseroNormalize Creating new pipeline
BraseroNormalize called brasero_job_set_current_action
BraseroNormalize New decoded pad linked
BraseroNormalize gstbaseparse.c(2890): gst_base_parse_loop (): /GstPipeline:pipeline10/GstDecodeBin:decodebin10/GstFlacParse:flacparse10:
streaming stopped, reason not-negotiated
BraseroNormalize called brasero_job_error
BraseroNormalize finished with an error
BraseroNormalize asked to stop because of an error
	error		= 1
	message	= "GStreamer encountered a general stream error."
BraseroNormalize stopping
Session error : GStreamer encountered a general stream error. (brasero_burn_record brasero-burn.c:2856)
```

When trying to use XFburn, the application crashes.

Any comment onhow to fix the problem is welcome. Thanks.

KK

---

### Post by ibjsb4 on 2013-01-05
I can understand Brasero not wanting to work, but not xfBurn.  What kind of errors do you get when opening it from terminal?

Also k3b is quite dependable.

---

### Post by fdrake on 2013-01-05
i don't like brasero too much and the error doesn't say a lot. Why dont you try k3b or gnome baker

k3b install
```

sudo apt-get install k3b

```

gnome baker
```

sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 8472BD8C
sudo su
echo "deb http://ppa.launchpad.net/gnomebaker/stable/ubuntu oneiric main deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu oneiric main" >> /etc/apt/sources.list.d/gnomebaker.list
exit
sudo apt-get update && sudo apt-get install gnomebaker

```

---

### Post by offgridguy on 2013-01-05
Glad to hear about the options, i gave up on Brasero myself and have been using windows
to burn my CD's.

---

### Post by Ken Kaniff on 2013-01-05
> **ibjsb4 said:**
>  What kind of errors do you get when opening it from terminal?

I didn't have a chance to open it that way. 
Thanks for the answer.



>  
Originally Posted by **Fdrake**
Why dont you try k3b or gnome baker.

Fdrake, thank you for the suggestion and the install code. k3b works great.

---

### Post by ibjsb4 on 2013-01-05
Nice  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Warprunner on 2013-01-05
Years ago, before I went totally Linux, I used Nero. Great program. Recently I found Nero Linux. 

Find it here: [http://linux.softpedia.com/get/Desktop-Environment/Tools/NeroLINUX-2506.shtml]("http://linux.softpedia.com/get/Desktop-Environment/Tools/NeroLINUX-2506.shtml")

While I haven't tried it yet, I assume it's great along with it's Windows sister program. 
You may want to check it out.

Maybe try K9Copy? Heard that was a good program too.

Best of luck!

---

### Post by thenanodude on 2013-02-17
Double check that the CD is not mounted before you run xfburn.  I was having crashing problems and discovered xfce automatically mounted the blank CD when I inserted it.  A quick "unmount" from a Thunar file browswer seemed to fix it.

---

### Post by bswilson on 2013-06-05
I had the exact same problem as the OP just recently (in the last month). The brasero error log was exactly the same. I was going to post even more details here because I also met with failure using K3B and attempting to burn my media from CDBurnerXP on a Windows XP VirtualBox Guest - nothing worked.

However, this last round of apt-get updates seem to have fixed K3B for me, but I still can't use brasero...

---

### Post by rocketeer141263 on 2013-06-17
I have suddenly started to have problems using xfburn. I am running Xubuntu 12.04 LTS. The problem is that having selected the file and the write speed, I hear the drive spin up. However xfburn indicates a write speed of 0.0. Pressing Cancel results in xfburn Aborting for ever.

Running xfburn from terminal gives the following output:-

**richard@grumpies-toy:~$ xfburn**

(process:1975): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/goption.c:2179: ignoring no-arg, optional-arg or filename flags (8) on option of arg-type 0 in entry (null):version

(process:1975): GLib-WARNING **: /build/buildd/glib2.0-2.32.3/./glib/goption.c:2179: ignoring no-arg, optional-arg or filename flags (8) on option of arg-type 0 in entry (null):main
** Message: Using UDEV
** Message: Using gstreamer transcoder.

Can someone suggest a possible reason and also a solution please.

UPDATE
Two error messages were posted as follows

There is data that needs to be written to the device "Blank DVD-ROM" before it can be removed. Please do not remove the media or disconnect the drive.
Error ejecting: eject exited with exit code 1: eject: unable to eject, last error: Inappropriate ioctl for device

---

### Post by shantiq on 2013-06-18
if any of you guys are looking to copy music cd
this is the most quiet [i can hardly hear any noise] way i have found to this day

all in terminal


RIP with ICEDAX [any version of Ubuntu]
===========


To copy an audio CD in the most accurate way, first run to rip


       ```
icedax dev=/dev/cdrom -vall cddb=0 -B -Owav

```

       and then to write run


```
wodim dev=/dev/cdrw  -v   speed=2 -dao -useinfo -text  *.wav
```



NB    you will be left with the rip wavs in your home folder
remove manually or making **ABSOLUTELY** sure you have no other files or folders containing the word "audio"   run  ```
rm *audio*
```

---

