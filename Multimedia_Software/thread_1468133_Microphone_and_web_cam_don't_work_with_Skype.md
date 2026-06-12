---
title: "Microphone and web cam don't work with Skype"
date: 2010-05-01
forum: Multimedia Software
---

### Post by rbaleksandar on 2010-05-01
Hi, guys.

  Just made a clean installation of the new Ubuntu 10.04 LTS this morning. So far, so good. Things are working smooth but there is one thing that bothers me - Skype (latest version). Here's a list of what's wrong:

NOTE: Can't remember if I used this verion of Skype in Ubuntu 9.10.

[LIST=1]
[*]Although Ubuntu recognizes the integrated **microphone**, Skype refuses to use it. Didn't have such problems before installing the new Ubuntu.
[*]**Web camera** (integrated Chicony USB 2.0) is not working with Skype (*worked in Ubuntu 9.10 though*). Haven't tested it with other applications yet but it appeares in the Multimedia Systems Selestor as default input device, so I guess it's recognize by Ubuntu.
[*]Activating **Screen Sharing** in a video call leads to crash (instant when I choose _full screen sharing_ and delayed with 1-2 min if I choose _selection of the screen_).
[/LIST]

  Any ideas guys? I repeat - didn't have any of these problems before. Oh, and one more thing - does Skype support ALSA? Because although I have some programs using ALSA (evidance that ALSA's working) I don't seem to be able to choose from Skype's settings to use ALSA and not Pulseaudio. I wanted to try ALSA because maybe the problem is in Pulseaudio.


Thanks a lot in advance! ^^



EDIT: I tried with Cheese. The diod on the camera lights up but there is now picture. So this isn't just a Skype issue.

---

### Post by winecurmudgeon on 2010-05-01
Same problems. Skype won't let me choose my web cam for sound, though it recognizes it for video and it seems to work. The only choice is "pulse-audio server (local)."

---

### Post by sixthwheel on 2010-05-01
I'm brand new to Skype, {since last week}.
My microphone works fine, and I'm going out to buy a webcam tomorrow.
Wonder if I should hold on till this is fixed.

---

### Post by oldsoundguy on 2010-05-01
Another one with dead Skype .. using Logitech Pro 9000.  Camera works in Cheese .. won't even turn on and no sound in Skype.(removed the non working one from synaptic and installed the one from Skype .. still no joy!)

This is the ONLY thing I have found thus far that has gone south in  10.04

Thus far .. when I use the Skype set up utility I get a video display.. camera comes on .. still no audio using the utility.
When I try and launch the camera from Skype itself, NO video and (of course) no audio.  And the camera doesn't even come on.

---

### Post by winecurmudgeon on 2010-05-02
I think I found the solution. Go to System/Preferences/Sound and select the camera under input device. Then turn the volume up as high as it will go. I did this, and Skpe seemed to work.

---

### Post by rbaleksandar on 2010-05-02
> **winecurmudgeon said:**
> I think I found the solution. Go to System/Preferences/Sound and select the camera under input device. Then turn the volume up as high as it will go. I did this, and Skpe seemed to work.


lol Actually it just worked now. The microphone I mean. :D I seriosly don't know what happened. I played with the **Multimedia Systems Selector** (MSS for short) (chose different drivers for the device) but at the end I returned the same settings I had at the beginning. Than I told myself: "If there is God, when I make a test call, I'll hear my voice from the speakers.". Obviously there is Heaven and God for when I made the test call and it recorded my voice, it played it without a single problem. :lolflag: The issue that remains - webcam that worked in previous Ubuntu doesn't work now. It's recognized by Ubuntu but shows no image or just a black screen. I'll have to do some research. Maybe a driver is corrupted/buggy and will have to use an older one.

PS: The question about Skype and Pulseaudio still remains too. It shows that it uses Pulseaudio although I'm pretty sure that when I choose from the MSS for the input device to use ALSA, it uses it. I know that because when I use Pulseaudio for the recording, I get bad sound (lots of cracking and noise). When I use ALSA, I don't have such issues.

---

### Post by chrispche on 2010-05-03
How do you install ALSA for use with Skype under 10.04. I must have a microphone working.

---

### Post by chrispche on 2010-05-04
Anyone?

---

### Post by tom purl on 2010-05-05
I'm having the same issue with only having the PulseAudio option and Ubuntu 10.4.  

I just upgraded Ubuntu (to 32-bit 10.4), and my previous Skype installation wasn't working, so I installed the 2.1 beta, which seems to be my only choice.  

Now, my microphone and headset don't work.  When I look at the "Sound Devices" configuration screen, my only option is "PulseAudio server".  I don't know anything about this server, and it is not what I've used in the past.

Any help would be greatly appreciated!

Tom Purl

---

### Post by tom purl on 2010-05-05
I think I may have fixed my problem.  I'm still not able to use any other driver than "PulseAudio" in Skype, but now Skype works for me.

First, I installed the "pavucontrol" package via apt-get.  This allows you to tweak your PulseAudio settings.  I then opened this app and tweaked my "Output Devices" and "Input Devices" tabs.  And now I can use Skype with my microphone and headphones.

Please note that I don't use Skype with a webcam, so I can't help with that.

---

### Post by powerofpi on 2010-05-05
Thanks for the suggestion, tom purl. That was my workaround that had previously allowed me to use Skype 2.1 with Ubuntu 9.10. However, after the upgrade to Ubuntu 10.4, sound was no longer working at all, so I had to delete the hidden .pulse folder in my home directory. Now no amount of fiddling with the pavucontrol will allow my mic to function. The only audio devices seen by Skype are PulseAudio server (local). 

My mic works fine in the system sound recorder app, but not in Skype now that I am using Ubuntu 10.4. Any suggestions would be greatly appreciated. Using an Acer Aspire One netbook, if it matters.

---

### Post by powerofpi on 2010-05-05
I solved my problem! Apparently my internal mic is single channel source, but the pulse audio volume control was treating it like it had a left and right channel, and the "left" and "right" channels were out of phase and were canceling one another. Decreasing the volume of one of the channels to zero fixed my problem completely. I now have loud and clear mic volume in Ubuntu 10.4 with Skype 2.1.

---

### Post by itziar on 2010-05-09
> **powerofpi said:**
> I solved my problem! Apparently my internal mic is single channel source, but the pulse audio volume control was treating it like it had a left and right channel, and the "left" and "right" channels were out of phase and were canceling one another. Decreasing the volume of one of the channels to zero fixed my problem completely. I now have loud and clear mic volume in Ubuntu 10.4 with Skype 2.1.

Thank you very, very much! I have an Aspire One too, and that worked for me! Thanks!

---

### Post by Happibun on 2010-05-09
I'm running an Aspire A1 too, and I can't seem to get my webcam working. Has anyone got any ideas why that might be?

I can not get it to work in Skype, Cheese, or Ekiga. 

The system says I have a USB 2.0 Camera (/dev/video0), Ekgia is more specific and lists two webcams USB 2.0 Camera (PTLIB/V4L) and (PTLIB/V4L2), neither of which work when selected.

I'm sorry, I'm stumped. What do I need to install to get this working?

Thanks, Jo

---

### Post by no2498 on 2010-05-09
Happibun 
try this
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test buttom for each 1

should have come on

try the cam in cheese

skype may take more help that i cant give

---

### Post by kaspin on 2010-05-10
[FONT="Comic Sans MS"][COLOR="Blue"][SIZE="2"]Hi 2498,
Thanks for that. Typing "gstreamer-properties" brought up a window where I clicked on 'Video'. Under 'video in' I left the default plugin (Video for Linux2 (v4l2)) and selected my Creative webcam from the drop down box. The test worked a treat.:P
But it still won't work in Skype (pressing 'test' produces a flicker of the green 'on' light, then nothing).:(
Let's hope there's a Skype expert out there...........
kaspin [/SIZE][/COLOR][/FONT]

---

### Post by no2498 on 2010-05-10
now you need the skype work around
open a terminal type, LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

hope this helps

---

### Post by timcredible on 2010-05-16
i have a logitech quick pro 9000 webcam, i've tried everything i can find, and still no option in skype to use the webcam for audio input.  works fine in ekiga and all the sound preferences tools see it just fine.  i have the webcam chosen under system->preferences->sound and tried the lowering of a channel to 0 in pulse audio preferences, still no option for the webcam as an input device.  this used to work, and works fine in ekiga, so it's got to be a skype issue.  i posted on the skype board also, but they never do anything about anything.  i guess it's back to forcing my family and friends and their friends to install ekiga.  seems stupid from a skype point of view - they are forcing people away from their product.

---

### Post by nolo on 2010-05-17
tim,

I'm assuming you are still on Jaunty.  I had the same issue as you in Jaunty.  I used the instructions on this [page]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html") to add additional sound apps to jaunty.  Using the device chooser I created a new profile for my webcam audio input and analog output.  After I upgraded to Karmic, this was no longer necessary. I use Skype several times a week with the same webcam as you for video conferences with our Corporate mucky mucks.

Hope this helps,

Nolo

BTW:  Ignore the audio settings in Skype, fix 'em in Audio Manager and they should work in Skype.

---

### Post by xtremedementor on 2010-05-17
Wow thanks for this post. I have been looking for a solution to this for ages.

Ubuntu NBR 10.04 
ASUS EeePC 1001HA

Installed pavucontrol (Pulse Audio Volume Control) from Ubuntu software centre.
Opened Pulse Audio Volume Control.
Set my input device volumes Left 100% Right 17% 
Unchecked lock together and set fallback mode icons.
Opened Skype and made a test call.

All is well and good.

Thanks again
:)

---

### Post by drslimw on 2010-05-17
I run in the same problem concerning the Webcam and Skype. The problem seems to be related to skype using old V4L library.
The solution would be to preload the compatible library in the skype's environment.

To Do

- create the following file 
          /usr/bin/skype.v4l.sh


- edit it with gedit and type

```


#!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
skype

```- save the file and make  it executable

- Go to Gnome Menu and edit the Skype launcher, so it will execute our new shell script

That worked for me!

---

### Post by pjrodz on 2010-05-23
> **powerofpi said:**
> I solved my problem! Apparently my internal mic is single channel source, but the pulse audio volume control was treating it like it had a left and right channel, and the "left" and "right" channels were out of phase and were canceling one another. Decreasing the volume of one of the channels to zero fixed my problem completely. I now have loud and clear mic volume in Ubuntu 10.4 with Skype 2.1.

this worked for me too! powerofpi you are the man! :guitar: i installed pavucontrol first then followed your instructions. i'm currently using ubuntu netbook edition 10.4 on my acer aspire one ZG5.

---

### Post by Happibun on 2010-07-23
Thank you [no2498]("http://ubuntuforums.org/member.php?u=906707"),

> open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test buttom for each 1


try the cam in cheeseWorked fine for me and got my webcam working, but you were right, Skype needed more. I tried the solution that you and [drslimw]("http://ubuntuforums.org/member.php?u=1073182") suggested:

> To Do

- create the following file 
          /usr/bin/skype.v4l.sh


- edit it with gedit and type

     Code:
     #!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
skype 
- save the file and make  it executable

- Go to Gnome Menu and edit the Skype launcher, so it will execute our new shell script
but I keep getting this error in a terminal when I try and test the webcam in Skype: 
> X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) 

I am probably missing something really obvious, sorry. Can anyone decode this and put me back on track?

Thank you for your help so far, I really appreciate it.

Jo

---

### Post by zazootheparrot on 2010-08-20
> **drslimw said:**
> I run in the same problem concerning the Webcam and Skype. The problem seems to be related to skype using old V4L library.
The solution would be to preload the compatible library in the skype's environment.

To Do

- create the following file 
          /usr/bin/skype.v4l.sh


- edit it with gedit and type

```


#!/bin/sh
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

 
skype

```- save the file and make  it executable

- Go to Gnome Menu and edit the Skype launcher, so it will execute our new shell script

That worked for me!

I have the same problem with my webcam when using skype. I tried what you have said  but unfortunately I don't know how to execute the file (I'm an absolute beginner:???:).
When I type the address in the terminal it gives the following message: 
```
bash: /usr/bin/skype.v4l.sh: Permission denied
```Could you please tell me how to execute the file?
Thank you in advance

---

### Post by zazootheparrot on 2010-08-22
I have solved the problem with executing the file but the webcam still doesn't work. 
Any help?

---

### Post by zazootheparrot on 2010-08-24
Bump   :?:

---

