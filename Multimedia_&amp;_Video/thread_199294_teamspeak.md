---
title: "teamspeak"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by spartan777 on 2006-06-18
i'm having trouble using teamspeak. i've read many other howto's but they depend on a setup, that someone has one device that works as the input and output. instead, i have a audigy 2 for output, and a logitech usb mic for input. i can run teamspeak while other programs like xmms are running, but can't use my mic. is there a way to have seperate devices for input and output?

---

### Post by yager on 2006-06-18
[QUOTE=spartan777]but can't use my mic.[/QUOTE]

Did you check that the microphone volume is turned on?  The default is to have the mic off.

Right click on the volume control next to the clock and pick Open Volume Control.  Check that the microphone volume is enabled and 100%.

If after adjusting, the volume is very low, here is a quote from Erik1397 from another thread.

[QUOTE=erik1397]double click on the volume icon, and go to Edit > Preferences, and make sure the following are ticked: Master, PCM, Line-in, CD, Microphone, Mic Boost, PC Speaker, and Capture. Then close that, and mess around with the volume of each one until u can hear your recording, using this program: applications >sound & video > sound recorder.[/QUOTE]

---

### Post by spartan777 on 2006-06-18
thanks, but this is the error message i get when i try to run "Sound Recorder:"

Your audio capture settings are invalid. Please correct them in the Multimedia settings.

---

### Post by yager on 2006-06-18
Sorry for t long delay in responding.  I searched for your error and found this in another thread.  Here are some instructions to try.

[QUOTE=Bukunut]Re: Microphone / Recording issues
Keidash

From your console type alsamixer when the page is open press F4 this will open the capture page. Use your right and left keys to scan across the columns to turn up the volume on each column use your up key. When you have finished press esc.
Check your settings on the first page of alsamixer too, scan across the columns look what maybe switched off [MM] use 'm' on your keypad to switch on, again to switch off.[/QUOTE]

Also, based on the thread, Soundrecorder is not really the best tool for testing the microphone in Dapper.  Refer to the thread for more info.
[http://ubuntuforums.org/showthread.php?t=147778&highlight=%22audio+capture%22+invalid](http://ubuntuforums.org/showthread.php?t=147778&highlight=%22audio+capture%22+invalid)

---

