---
title: "Jack will not capture sound"
date: 2011-08-29
forum: Multimedia Software
---

### Post by gusbeto37 on 2011-08-29
Hi all, I have been searching the forums for about an hour now and nothing seems to work. Please Help!

I am using a Mackie Onyx Blackjack. 

All levels are correctly set, settings set to the correct sound card. Now the real problem is not apparently communicating with it because if I select it on "Playback Only" Aqualung does reproduce music and everything else also does. But when I put "Capture only" or "Duplex" it seems to crash. Here is the log of the messages:

[QUOTE="Jack Message"]20:46:24.405 JACK was started with PID=2537.
loading driver ..
SSE2 detected
apparent rate = 22050
creating alsa driver ... hw:1,0|hw:1,0|1024|3|22050|2|2|nomon|swmeter|-|32bit
control device hw:1
20:46:24.584 ALSA connection change.
configuring for 22050Hz, period = 1024 frames (46.4 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
20:46:24.849 JACK was stopped successfully.
20:46:24.850 Post-shutdown script...
20:46:24.850 killall jackd
jackd: no process found
20:46:25.263 Post-shutdown script terminated with exit status=256.
20:46:26.778 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
20:46:37.758 Startup script...
20:46:37.759 artsshell -q terminate
sh: artsshell: not found
20:46:38.162 Startup script terminated with exit status=32512.[/QUOTE]

And here is the error message:

[QUOTE="Error Window"]Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.[/QUOTE]

Now here is the result of aplay -l

[QUOTE="aplay -l"]gustavo@la-buena:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Blackjack [Onyx Blackjack], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/QUOTE]

If there is any other information you'd like me to give you, please do not hesitate to ask.Anyone has any idea of what is happening there :confused::confused:

---

### Post by radkins2 on 2011-08-29
> **gusbeto37 said:**
> Hi all, I have been searching the forums for about an hour now and nothing seems to work. Please Help!

I am using a Mackie Onyx Blackjack.[[color=black]indiana recording school[/color]](http://azmythmusictech.com)

All levels are correctly set, settings set to the correct sound card. Now the real problem is not apparently communicating with it because if I select it on "Playback Only" Aqualung does reproduce [music recording school]("http://azmythmusictech.com") and everything else also does. But when I put "Capture only" or "Duplex" it seems to crash. Here is the log of the messages:[[color=black]school[/color]](http://azmythmusictech.com)



And here is the error message:



Now here is the result of aplay -l



If there is any other information you'd like me to give you, please do not hesitate to ask.Anyone has any idea of what is [indiana recording studio]("http://azmythrecording.com") happening there :confused::confused:


I have a friend who had the same thing happen. He had to completely uninstall it and start over.

---

### Post by gusbeto37 on 2011-08-29
I do not want to get rid of this installation, since everything runs so good except for audio recording. 

But perhaps I will try to make another ubuntu partition (I got the space) later on the week and test if that is the problem.

As an additional piece of information I had previously purged and reinstalled both jack and alsa related things before posting the quotes I put above.

---

