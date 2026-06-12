---
title: "MythTV Backend Not Recognizing USB Penstick Tuner on Startup (Model 800e)"
date: 2012-05-27
forum: Mythbuntu
---

### Post by mythbuntukid on 2012-05-27
When the system starts for the first time (whether by a restart or by a  fresh boot after being shutdown), the mythtv backend for some reason  will not recognize one of my tvtuner cards: it is a Pinnacle Systems  HDTV USB penstick, model 800e.
 
I currently have two tvtuners in the system, my other is a Pinnacle  Systems PCI 800i.  I have tried removing the 800i, but that doesn't seem  to affect the backend's ability to recognize the USB penstick.
 
The weird thing is that after I boot up, I can manually restart the backend and  mythtv will see the USB penstick just fine.  The problem is that when I  am not home and need to have the system automatically record something,  the system will automatically wake itself up (ACPI) as expected, but since the  USB penstick does not automatically initialize on this first boot, the  recording fails.

Ubuntu otherwise seems to load/find the USB penstick because lsusb -l lists the device just fine after the computer boots up.
 
So at this point I am stuck.  My hunch is that the backend is starting  up before the USB penstick is initialized by Ubuntu, but I really don't  know and I'm really not sure where or how to investigate the problem.   I'm not really an expert, but I can find my way around linux (been using  mythtv for about 6 years now) . . . so if someone has suggestions, or  needs more information, just let me know and I should be able to post back info that might be helpful in diagnosing the problem.  Any help  would be greatly appreciated.
 
I'm running mythdora 64-bit 12.04 mythtv 0.25 on an AMD 64 bit system.
 
Thanks in advance.
 
mythbuntukid

---

### Post by nickrout on 2012-05-27
Yes you have probably identified the issue. It is dealt with extensively in this forum. Easiest thing is to put a delay in the startup of mythtv-backend, either a simple time delay (sleep N) or a test to see if all expected dvb devices are up.

---

### Post by mythbuntukid on 2012-05-27
Nick:

I tried using the delayed start identified in this link: [http://ubuntuforums.org/showthread.php?t=1461705](http://ubuntuforums.org/showthread.php?t=1461705)

Specifically, I modified [COLOR=Red]/etc/init/mythtv-backend.conf[/COLOR] by inserting "sleep 4" before "/usr/bin/mythbackend"

When I boot the computer up, I get the following message immediately after mythwelcome starts: "Could not connect to the master backend server.  Is it running?"  That message goes away shortly thereafter.

I think this means the "sleep 4" function is working and has delayed the start of the backend at startup.

But, the bad new is that this change did not resolved my problem.  The 800e tvtuner is still not working at startup.

Here's an interesting twist.  Before, to get the 800e to work, I would go into the backend setup whereby I would get the following message:

"WARNING: The backend is currently running.  Changing existing card inputs, deleting anything, or scanning channels may not work."

I am then given the following options: (a) Stop Backend and Continue"; (b) Continue"; or (c) Exit.

In the past I have always selected (a).  In this case, I'm assuming the system shuts down the backend while I do my editing, then when I exit the backend setup, the backend server is restarted.  I then to back in and restart mythwelcome/mythfrontend and everything seems to be working just fine.

This time, out of curiosity, I selected (b) so that the backend was not stopped.  I then immediately exited the backend setup and went back to mythfrontend (which was still running BTW) and the 800e tv tuner was working and able to tune.  I didn't even need to restart mythfrontend.

I'm at a loss . . . any suggestions?

---

### Post by mythbuntukid on 2012-05-27
Now that I'm looking at it, when I start the backend setup I am prompted immediately to shut down all backend processes.  So, when I get into the actual backend setup and I am presented with menu options (a)-(c), the backend server has already been shutdown.

Long story short, there's no "interesting twist" - if I restart the backend after the initial boot, the tv tuner card works fine.  Even delaying the backend startup does not fix this problem - it must be restarted once the system is up and running.

---

### Post by nickrout on 2012-05-27
OK fixing one problem leads to another... delaying the backend startup leads to the frontend starting up before the backend is ready. *sigh*.

How many dvb devices do you have once all tuners are loaded? Say it might be two as i think you said you have two tuners. We therefore need to wait for /dev/dvb/adapter1/frontend0 to exist, at which stage we know both have come up (the first will be /dev/dvb/adapter0)

Instead of a sleep 4, try something like

while [ ! -e /dev/adapter1/frontend0 ]
do
sleep 1
done


Once you have the backend not starting until both cards are there, you can sort out a delay for the frontend/mythwelcome.

---

### Post by mythbuntukid on 2012-05-27
Nickrout - thank you for the reply

I do have two adapters that are loading.  In mythtv, the configuration looks like this:

/dev/dvb/adapter0/frontend0 (this is the 800i card)
/dev/dvb/adapter1/frontend0 (this is the 800e card)

I added the code as you suggested:
while [ ! -e /dev/adapter1/frontend0 ] do sleep 1 done

replaced:

sleep 4

Now, after rebooting the computer, I get the same error as before:

Could not connect to the master backend server.  is it running?  Is the IP address set for it in mythtv-setup correct?"

This box used to disappear after a few seconds; now it is not disappearing at all.

If I follow your code correctly, we are telling the backend to hold off on starting until the "adapter1" loads.  As such, it doesn't look like the "adapter1" is loading and, therefore, the backend isn't turning on . . . hence, the box stays up and I continually receive master backend connection errors. :(

---

### Post by nickrout on 2012-05-27
PS why are you starting mythtv-setup all the time?

---

### Post by mythbuntukid on 2012-05-27
The only time I have been running mythtv-setup is to get the 800e capture card working.  The only other time I run it is to configure my settings (channels, etc.).

FYI - when the computer wakes itself up (ACPI) from being turned off, it boots into mythwelcome.

---

### Post by mythbuntukid on 2012-05-27
After restarting the computer, I did a dmesg in terminal and it returned the following error:

[  104.563516] lgdt330x: i2c_read_demod_bytes: addr 0x0e select 0x58 error (ret == -19)

In doing a search for "lgdt330x: i2c_read_demod_bytes:", I found the following website:

[http://www.kernellabs.com/blog/?p=1092](http://www.kernellabs.com/blog/?p=1092)

I know the tvtuner is the wrong one (I'm obviously not using an ATI), but I noticed several items that seem to be similar to my problem:

Note the entry from "Dan G" on December 2, 2009 4:00 a.m. - he has the same error that I'm getting and his "workaround" is to immediately restart mythtv-backend after booting and his tvtuner card works.

The last entry from "Larry" indicates that he "blacklisted" the "em28xx-alsa", "em28xx-dvb" and the "em28xx" and then modprobed them in MythTV.

I know that the 800e runs on the em28xx chipset (I recall having to manually install the drivers probably 5 or 6 years ago).  My last go around with mythtv, the drivers were automatically loaded (in fact, I'm sure they are because it appears in the "firmware" and lsusb correctly finds the tvtuner card).

I tried to "blacklist" as mentioned by "Larry", but if I do that, the adapter doesn't show up at all.  That is, if I go into the frontend and try to change the Input, the adapter assigned to the 800e doesn't show up at all - it looks like I just have one adapter.  If I boot like I have been, the adapter shows up, it just can't tune to the channel unless I restart the backend like mentioned before.

Maybe this will provide some help?

---

### Post by mythbuntukid on 2012-05-27
One other note, after I restart mythtv-backend, I did dmesg again, and the following two lines are added at the bottom after the error in my previous post:

[ 1090.876027] xc2028 2-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[ 1091.932723] xc2028 2-0061: Loading firmware for type=D2633 DTV6 ATSC (10030), id 0000000000000000.

The tvtuner (800e) works as I have mentioned before after I do the restart - so maybe the two lines above provide some indication of what's going on?

---

### Post by nickrout on 2012-05-27
One thing to remember - generally the firmware does NOT get reloaded if you warm boot, ie rebooting without turning the power off. With a usb card it might also work to unplug the card and plug it back in again while the compter is doing the bios check.

What seems to be happening is some kind of race condition where for some reason the module cannot load unless you wait a while after other modules have loaded. You can use one of the two solutions on offer, but the easiest seems to be to put a ```
service mythtv-backend restart 
``` in /etc/rc.local. That gets executed after all other startup scripts.

Oh and for a better fix I suggest the mythtv-users mailing list, Devin Heitmuller hangs out there and may respond. He is the driver guru (as you can see from the kernellabs page you pointed to)

---

### Post by mythbuntukid on 2012-05-28
Nickrout:

The command does appear to be working - I just didn't wait long enough.  This is a great first step.  It takes about 2 minutes for the system to restart the backend.  BUT, please note that I needed to use the following command:

sudo service mythtv-backend restart

in the /etc/rc.local file to get it working (I added "sudo" to be beginning.

Question - is there a faster way to get it to restart?  2 minutes is a long time at startup . . . but hopefully I can configure everything so it will record while I'm gone.

---

### Post by mythbuntukid on 2012-06-08
I'm still having periodic problems with the above fix because the system still won't recognize the 800e tvtuner sometimes.

So in looking into this further, I have been doing some tinkering and here's what I've found out so far:

I thought it might be a good idea to try and reload the v4l-DVB drivers.  In doing this, I noticed that I had the "DVB" option selected for proprietary drivers in the "Additional Drivers" option under "Settings" under "Applications".  I proceeded to deselect that option so that the system defaulted back to the regular open source drivers (i.e., not the proprietary drivers that can be selected under that option).

Upon restart, the system would boot into mythwelcome just fine and then the hard drive would light up like a Christmas tree and the system would basically freeze.  I can't even do a ctrl-alt-del (or backspace) to reload or restart; I needed to do a hard reset.

So my thinking is that there's something wrong with the the DVB driver that's affecting how the 800e gets loaded.  I still have not figured out how to reload the proprietary driver because I'm in a catch-22 situation - if I don't have the unit plugged in when I start the system, I don't get the option.  If I do plug it in, the system freezes so I can't go select it.

So, in looking for a better solution (and to get this driver/tuner working again) - anyone have any ideas?

Thanks,
BJ

---

