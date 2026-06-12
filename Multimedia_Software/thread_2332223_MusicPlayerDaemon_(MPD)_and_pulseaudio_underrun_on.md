---
title: "MusicPlayerDaemon (MPD) and pulseaudio: underrun on 16.04"
date: 2016-07-29
forum: Multimedia Software
---

### Post by spazzeri on 2016-07-29
Hello,

On Ubuntu 16.04 I installed mpd (version 0.9.12) from the repositories.

This setup in mpd.conf worked in Ubuntu 14.04:

```

audio_output {
    type        "pulse"
    name       "pulse output"
}

```

On the same machine now running 16.04 I added:
```
mixer_type "software"
```
-- before that setting the volume failed (through mpc volume for example).

Problem: audio playback now stops very often.

Pulseaudio sends error messages like the following:
```

pulseaudio[21406]: Processing rewind...
pulseaudio[21406]: Implicit underrun of 'pulse output'
pulseaudio[21406]: alsa_output.pci-0000_00_1b.0.analog-stereo: Found underrun 27572 bytes ago (9472 bytes ahead in playback buffer)

```

Do you have ideas about how to fix this ?

---

### Post by yoshii on 2016-07-29
I don't know for sure, but I do music mixing / recording with Ubuntu Studio using PulseAudio.  
One thing I had to do was to... 

$ sudo mousepad /etc/pulse/daemon.conf

or 

replace "mousepad" with gedit or leafpad or whatever text editor you have installed.  

After /etc/pulse/daemon.conf is loaded in your text editor, scroll down to the section that looks something like this:

```

default-fragments = 8
default-fragment-size-msec = 10

```

Those two number get multiplied together to create product sum which represents the total pulseaudio buffer size in milliseconds.  
For technical reasons, the default-fragments of audio usually works better with 2 or 3 (instead of 8).  
And the default-fragment-size-msec in in your case should probably be set higher.  

Both sections need to be uncommented.  That is, delete the "; " before the text at the start of the line, so that the changes are actualized.  
The texts as they show up in a fresh install are defaults.  

But getting back to the variables again, on my Ubuntu Studio system, I set the first number to 2 and the 2nd number to 4 for a total of 8 milliseconds.  (2x4=8)
This created a much lower latency (delay) for my system but at greater risk of buffer underruns unless other optimizations are done.  
This is a much much smaller buffer than the 80 millisecond buffer default.  In your case since there are buffer underruns instead of high latency issues.  So you will probably want to set the first number to 2 or 3 for compatibility and stability and set the second number to something like 2000 (I am guessing).  2 x 2000 = 4000, which is 4 seconds.  If the visual responsiveness of your system is then too slow, then you'd need to lower it to 2 x 400 or experiment with other values greater than a sum of 80 milliseconds, yet low enough to not be a problem in terms of delay.  

Also, if you haven't already,...

"$ sudo gedit /etc/fstab" (or use whatever text editor you have instead of gedit, just be sure to not save in a formatted text format, so probably avoid LibreOffice Writer or whatnot.  Use geany or leafpad or mousepad or gedit.  

Anyways, the idea is to text edit /etc/fstab and to add the "noatime" parameter to your main system drive's entry.  

For example, 
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                          <mount point>   <type>  <options>       <dump>  <pass>
UUID=eeeeaeee-eeee-eeee-eeee-eeeeeeeeeeee /               ext3    noatime,errors=remount-ro 0       1
UUID=eeeeeeee-eeee-eeee-eeee-eeeeeeeeeeee none            swap    sw              0       0

```

Be sure not to change anything else, and only add the "noatime," before "errors=remount-ro 0" etc.  Do not add any spaces.  
What this does is disable last file access time, which is an unneeded labor-intensive, input/output intensive process.  
Every time a file is read or written and possible even executed, it's last file access time is written to the filesystem.  
This isn't needed for most of us casual users, because we just rely upon the file creation date and file modification date, which are both independent and different.  

So with noatime (no access time) engaged, the excessive logging is disabled and hard drive (or SSDrive or FLASH drive) activity is reduced a lot, and there's more CPU time available for the system to do other things, and the drive buffers aren't used for the access logs.  

I hope I am explaining this right.  

Anyways, I read about this edit on a linux audio website that is out of date, but still has some decent tips mixed in with the obsolete ones.  

Also, you will want to disable any unneeded services.  
Some of them can be safely disabled in a reversible way by going into /etc/init/ (not init.d) and creating corresponding *.override files for those services you are sure you don't need.  For example, if you don't need bluetooth functionality, there is probably a "bluetooth.conf" file in /etc/init/ so you (using sudo) invoke your text editor and create /etc/init/bluetooth.override that contains a single line with the word "manual" (no quotes).  Save it and reboot and bluetooth should be disabled.  If you need bluetooth again, delete the bluetooth.override file (using sudo since that directory is protected).  

If you aren't sure if the service should be disabled or not, read it's *.conf file and look at the first several comments at the beginning of the file.  Here's a list of the *.override files that I created on a non-music system:  

> 
/etc/init/winbind.override
/etc/init/smbd.override
/etc/init/samba-ad-dc.override
/etc/init/reload-smbd.override
/etc/init/nmbd.override
/etc/init/cups.override
/etc/init/cups-browsed.override
/etc/init/avahi-cups-reload.override
/etc/init/bluetooth.override
/etc/init/apport.override


The first 5 are related to Microsoft Windows sytems and Samba, which I don't ever use at all.  
The next 3 ("cups") are related to printing, which I don't use that particular computer for.  
Apport reports errors to Cannonical, I guess.  I have that disabled because for whatever reason, my system is more stable without it.  
I have decided, if I get errors, I will know by system misbehaviour, and that is not a time to be using the internet to send messages to anybody.  

There are some other places and ways to disable things, but this is a decent start.  Hopefully by disabling what you don't need, more system resources (RAM, CPU power, filesystem activity reduction) are available to the programs and procedures you prefer.  

Also, you will want to try to set your CPU throttling to "performance" instead of "ondemand".  That should have a big effect also.  
I posted this info earlier and other optimizations here:

[https://ubuntuforums.org/showthread.php?t=2309922&highlight=informal+tips+daw](https://ubuntuforums.org/showthread.php?t=2309922&highlight=informal+tips+daw)

Good luck.  
Please mark this thread SOLVED if it works out.  If it doesn't work out others who are more knowledgeable than me will know what to do more than likely.  
FYI, I use PulseAudio instead of JACK for using 32-bit Windows's REAPER to compose electronic music with VST instruments and effects.  I don't record multitrack audio, but I mix and playback multitrack audio and process it alongside MIDI controlled VST instruments.  I also needed to implement the "tsched=0" hack, which is also included in the link above.  

Sorry if this is a lot of information.  I just hope it works out.  Spread the word if it does.  Hopefully we can keep these important tweaks and optimizations in the Ubuntu Community zeitgeist since the original sources are getting so old and inactive now.  PulseAudio does have some flexibility but it involves these text edits.  

Peace

---

### Post by spazzeri on 2016-07-30
Well,

Thank you for your post, information is always welcome.

I made a fool of myself &#8230; I had forgotten to disable another pulse output to a currently shutdown machine.
Now that this output is disabled, mpd works fine.

---

