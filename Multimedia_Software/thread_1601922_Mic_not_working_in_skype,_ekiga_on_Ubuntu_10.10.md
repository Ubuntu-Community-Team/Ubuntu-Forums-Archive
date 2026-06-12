---
title: "Mic not working in skype, ekiga on Ubuntu 10.10"
date: 2010-10-20
forum: Multimedia Software
---

### Post by amirks on 2010-10-20
I have an Acer Aspire One netbook and have tried to enable my microphone without any luck. Surprisingly the Sound Recorder works perfectly but skype and ekiga are not able to transfer my voice. 
I have tried playing around with gnome ALSA mixer and PulseAudio Volume Control but nothin changes. Any help is greatly appreciated.

Thanks
Amir

---

### Post by ubulis on 2010-10-23
Hello!
Same issue...
¿Any ideas?

---

### Post by dianagk on 2010-10-24
Same with me. I was on 10.04 and had the same problem. Upgraded today, but the problem is still there.

---

### Post by steve-o1983 on 2010-10-25
> **dianagk said:**
> Same with me. I was on 10.04 and had the same problem. Upgraded today, but the problem is still there.

I had the same problem, especially with Skype.  After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control").  Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence".  That should solve the problem.  You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels."  That will throw it off every time.

---

### Post by dianagk on 2010-10-25
> **steve-o1983 said:**
> I had the same problem, especially with Skype.  After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control").  Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence".  That should solve the problem.  You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels."  That will throw it off every time.

Well, I did that, but all that I hear on my Skype test call is some noise. Not my voice, just some noise. I guess the mic is working, but how can I make it useful?

---

### Post by lidex on 2010-10-25
Check the first part of this blog post:
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

---

### Post by smithintaiwan on 2010-10-25
Same problem. I tried both of the above fixes. I'm on an Acer Aspire One 250. The webcam actually works fine, but the mic doesn't seem to at all.
Peace

---

### Post by garvinrick4 on 2010-10-25
Here is what was fix for mic.

---

### Post by smithintaiwan on 2010-10-25
Thanks Garvinrick, 
But for some reason I couldn't get the connector to change on mine. That field just didn't exist.
However, I just found a page that helped me get my mic going. The directions are: 
In terminal:

sudo apt-get install pavucontrol

pavucontrol


Then:

    * Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence.

Once in pavucontrol I just silenced the right channel mic and it worked immediately. I tested in Skype and all seems fine. This seems to be the same as Steve's answer above. Cheers Steve. 

Skype does seem a bit choppy in both directions though -at least it is not as clear as it is in Windows- but I think that's a different issue.
Hope this helps.

---

### Post by kennedyvelez on 2010-11-04
same here on my desktop, mic is down... help!

---

### Post by thenzero on 2010-11-04
Hey guys-

I was having a similar problem yesterday.  The solution for me was to open PulseAudio Volume Control, adjust the left channel to be muted, but leave the right channel at full volume.

See the thread here: [http://ubuntuforums.org/showthread.php?t=1612994](http://ubuntuforums.org/showthread.php?t=1612994)

---

### Post by ubey on 2010-11-25
> **smithintaiwan said:**
> Thanks Garvinrick, 
But for some reason I couldn't get the connector to change on mine. That field just didn't exist.
However, I just found a page that helped me get my mic going. The directions are: 
In terminal:

sudo apt-get install pavucontrol

pavucontrol


Then:

    * Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence.

Once in pavucontrol I just silenced the right channel mic and it worked immediately. I tested in Skype and all seems fine. This seems to be the same as Steve's answer above. Cheers Steve. 

Skype does seem a bit choppy in both directions though -at least it is not as clear as it is in Windows- but I think that's a different issue.
Hope this helps.
Thank you, for the first time in four bloody months i got Skype to work properly.
I can not see **why **it helps, but it does.
It is not necessarily the right channel, you can silence the left and it works fine too.
Can someone explain to me **why** this fixes the problem?
Thank you, again!

---

### Post by BigD77 on 2010-11-25
Don't know if this will help, but what i did was go into System/Preferences/Sound and looked into the tab input and highlighted Internal Audio Analog Stereo.  At least that's what my laptop had.  Once highlighted (Clicked on) the mic worked on Skype.  Funny, but that's all I did.

---

### Post by Finn bjerke on 2010-12-06
My Labtop has mic problems as well I use Ubuntu 10.10

1. First no sound I installed Pavucontrol and I got sound from mic til Skype and other reocrindg programmes
2. Sound is however noisy sounds like and Old LP, crackling kind of noises.
3. Using external mic makes noise worse. 
4. trying ALSA mixer made no difference. 

Googling this problem indicates that a lot of users have this problem, så maybe bugfixes are needed more than say Upgrades every half year?  Tis a little frustating, I skype a lot. Mics should work inUbuntu environment ....

---

### Post by mistapee on 2010-12-11
Lots of hassles getting the mic going.  Followed all the suggestions related above.  I'm not sure which one did the trick, but I finally went to the volume control on the top bar and made adjustments in 'preferences' and we're away.  Thanks to the previous contributors.  In learning about mics, I also learned a few tricks in Ubuntu with sound generally.

---

### Post by niccolas on 2010-12-11
> **smithintaiwan said:**
> Thanks Garvinrick, 
But for some reason I couldn't get the connector to change on mine. That field just didn't exist.
However, I just found a page that helped me get my mic going. The directions are: 
In terminal:

sudo apt-get install pavucontrol

pavucontrol


Then:

    * Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence.

Once in pavucontrol I just silenced the right channel mic and it worked immediately. I tested in Skype and all seems fine. This seems to be the same as Steve's answer above. Cheers Steve. 

Skype does seem a bit choppy in both directions though -at least it is not as clear as it is in Windows- but I think that's a different issue.
Hope this helps.

Thank you, this pavucontrol solved my problem immediately. I just click to sound icon in input devices tab and it work. It didn't need to change right or left channel. My laptop has 2 microphone so maybe it work because of them.

---

### Post by kblt on 2010-12-20
> **smithintaiwan said:**
> Thanks Garvinrick, 
But for some reason I couldn't get the connector to change on mine. That field just didn't exist.
However, I just found a page that helped me get my mic going. The directions are: 
In terminal:

sudo apt-get install pavucontrol

pavucontrol


Then:

    * Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence.

Once in pavucontrol I just silenced the right channel mic and it worked immediately. I tested in Skype and all seems fine. This seems to be the same as Steve's answer above. Cheers Steve. 

Skype does seem a bit choppy in both directions though -at least it is not as clear as it is in Windows- but I think that's a different issue.
Hope this helps.

...worked for me......!!!!! but.... the google voice plugin has an auto adjustment feature that resets the mixer levels!!! aaargh! ....now to figure out how to turn that off.....

---

### Post by markthekdeguy on 2010-12-21
fwiw, i had to install pavucontrol ..  but Pulseudio crashed far too often.
so as i dont like Gnome anyway, i went back to Kubunti 10.04 LTS
- Kubuntu 10.04 LTS neither needs or uses pulseaudio.
i am happily back on KDE 

here's something odd.
strange thing is install skype, do test call, works.
noted no 'digital' slider in the Kmix alsamixer
reboot, 
test call, no mic audio on skype.
noticed a new slider in kmix (Kde's nice ALSA mixer)
the digital' is actually 'mic gain'
works for hours flawlessly, with Amarok playing quietly in the background,
youtubes being played, DVB TV being watched in Kaffeine. etc.

this modest use of a soundcard would crash and burn under Ubuntu GNOME,
so if you've never tried KDE .. here's a reason, but not sure how
it would look on a netbook though :)
good luck.
Mark.

---

### Post by dudemena on 2010-12-29
> **steve-o1983 said:**
> I had the same problem, especially with Skype.  After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control").  Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence".  That should solve the problem.  You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels."  That will throw it off every time.

Thanks for the help.  Worked like a charm in an Acer Aspire one. I just had to make sure I showed all the input devices in order to follow your instructions in the pulse audio volume control window.

---

### Post by tunggo on 2010-12-30
> **kblt said:**
> ...worked for me......!!!!! but.... the google voice plugin has an auto adjustment feature that resets the mixer levels!!! aaargh! ....now to figure out how to turn that off.....

In order to make google voice to work do the following:

in 

~/.config/google-googletalkplugin

edit the file "options" (if it does not exist, create it) and put a line:

audio-flags=1

Restart and voila!!

Cheers.

---

### Post by Dinesh Rao on 2011-01-03
> **smithintaiwan said:**
> Thanks Garvinrick, 
But for some reason I couldn't get the connector to change on mine. That field just didn't exist.
However, I just found a page that helped me get my mic going. The directions are: 
In terminal:

sudo apt-get install pavucontrol

pavucontrol


Then:

    * Click the "input devices" tab. Click the lock icon to unlock channels. Set the front right channel to silence.

Once in pavucontrol I just silenced the right channel mic and it worked immediately. I tested in Skype and all seems fine. This seems to be the same as Steve's answer above. Cheers Steve. 

Skype does seem a bit choppy in both directions though -at least it is not as clear as it is in Windows- but I think that's a different issue.
Hope this helps.


Thank you very much. The above settings sorted out the issue of microphone on ASUS 1005 px.

-Dinesh

---

### Post by ksjc on 2011-01-16
pavucontrol works perfectly!!! THANKS! I was going back to windows for Skype, now I dont have too!!!

---

### Post by totoritko on 2011-01-31
Unfortunately, it didn't work for me. I'm using Ubuntu 10.10 and have an ASUS 1005PX, but setting the right-front channel on input devices to silence doesn't do anything - I can still see the input level meter floating around zero and I'm not able to hear anything in Skype. I'm quite desperate by now, as I seem to be the only idiot on the Internet with this problem... Can anybody help?

---

### Post by lidex on 2011-01-31
> **totoritko said:**
> Unfortunately, it didn't work for me. I'm using Ubuntu 10.10 and have an ASUS 1005PX, but setting the right-front channel on input devices to silence doesn't do anything - I can still see the input level meter floating around zero and I'm not able to hear anything in Skype. I'm quite desperate by now, as I seem to be the only idiot on the Internet with this problem... Can anybody help?

OK, I won't make any jokes...
There are more than one reason for mic issues in ubuntu - mainly hardware specific. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by totoritko on 2011-02-01
[http://www.alsa-project.org/db/?f=303fc7819a307122c0e82e5f22a66f09941a1a8b](http://www.alsa-project.org/db/?f=303fc7819a307122c0e82e5f22a66f09941a1a8b)

Thank you for any pointers on how to resolve this. When I played around with the inputs in padevchooser I cranked the input volume level up to 400% and could clearly hear noise, so apparently the driver is able to communicate with the card, but it only records very quiet noise...

---

### Post by totoritko on 2011-02-01
Using the output of alsa-info I found out that I have a HD-Intel codec model ALC259, which, according to [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) ,isn't supported - does that mean I'm completely out of luck? Or is there still hope of getting it work? Short of writing a new driver, I can fiddle around with kernel parameters and/or recompile alsa with tuning the code/headers around a bit. Thanks.

---

### Post by lidex on 2011-02-01
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by totoritko on 2011-02-02
Tried, but without any luck, I still can see no improvement in either pavucontrol (input levels still near zero) or Skype (no audible input). I suspect that there might be a problem with the BIOS-provided ACPI tree, since the kernel prints in dmesg:  hda_codec: ALC259: BIOS auto-probing. hda_codec: connection list not available for 0x24  and ASUS is quite an offender when it comes to messed up ACPI tables (once bitten by an older laptop model which wouldn't even boot Linux without turning ACPI off almost completely). I'll try to look for a newer BIOS version and flash it in.

---

### Post by lidex on 2011-02-02
Sounds like a plan. For some reason the codec is not properly recognized. If that fails, you can try an upstream kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by dazeddezzy on 2011-02-04
> **steve-o1983 said:**
> I had the same problem, especially with Skype.  After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control").  Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence".  That should solve the problem.  You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels."  That will throw it off every time.
thank you this worked for my issue.

---

### Post by Wesley Dawson on 2011-02-09
Wow thanks this worked for my acer aspire d260!! i appretiate the help.

---

### Post by legend_gibby on 2011-03-02
> **lidex said:**
> Sounds like a plan. For some reason the codec is not properly recognized. If that fails, you can try an upstream kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

right ok ive dont the stuff ya said in the previous tread this is what i got [http://www.alsa-project.org/db/?f=11a3d2b96e1f1ed18cf08f84ee3ff0fedeb168cf](http://www.alsa-project.org/db/?f=11a3d2b96e1f1ed18cf08f84ee3ff0fedeb168cf)

justa bunch of jumbeled up numbers and letters......

can ya help me please!?

---

### Post by lidex on 2011-03-02
> **legend_gibby said:**
> right ok ive dont the stuff ya said in the previous tread this is what i got [http://www.alsa-project.org/db/?f=11a3d2b96e1f1ed18cf08f84ee3ff0fedeb168cf](http://www.alsa-project.org/db/?f=11a3d2b96e1f1ed18cf08f84ee3ff0fedeb168cf)

justa bunch of jumbeled up numbers and letters......

can ya help me please!?

Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by legend_gibby on 2011-03-02
> **lidex said:**
> Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

ok cool ill give it a go later on......cheers

i take it @ this point i add my user name:(sudo apt-get install linux-alsa-driver-modules-$(uname -r))

---

### Post by lidex on 2011-03-02
> i take it @ this point i add my user namesudo apt-get install linux-alsa-driver-modules-$(uname -r)) 
No. Run as written.

---

### Post by legend_gibby on 2011-03-02
> **lidex said:**
> No. Run as written.

ok no problem .....ill give it a go and see!!!

cheers

---

### Post by legend_gibby on 2011-03-02
ok i did the first bit and the second bit and got this!!!

view screen shot!!!

---

### Post by lidex on 2011-03-02
That means you have another package manager running. make sure synaptic and update manager are closed and run the last 2 commands again, then reboot.

```
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

---

### Post by linuxr2k on 2011-03-08
Hey guys, Just wanted to put in a line. My mic had similar problems. In case your GUI is GNOME, download the GNOME ALSA MIXER from Applications --> Ubuntu Software Center.
Type the name in the search. After installing it. GOTO Applications -> Sound & Video -> GNOME ALSA MIXER. When the applet opens, locate the MIC and notice that it is muted. Just unmute the mic and voila !
After that it will definitely work. You can also test it via the Applications -> Sound & Video -> Sound Recorder.

---

### Post by atentik on 2011-03-08
> **dianagk said:**
> Well, I did that, but all that I hear on my Skype test call is some noise. Not my voice, just some noise. I guess the mic is working, but how can I make it useful?

I am unable to individually control left/right volume channels. How are you able to do it?

---

### Post by sammiev on 2011-03-14
> **linuxr2k said:**
> Hey guys, Just wanted to put in a line. My mic had similar problems. In case your GUI is GNOME, download the GNOME ALSA MIXER from Applications --> Ubuntu Software Center.
Type the name in the search. After installing it. GOTO Applications -> Sound & Video -> GNOME ALSA MIXER. When the applet opens, locate the MIC and notice that it is muted. Just unmute the mic and voila !
After that it will definitely work. You can also test it via the Applications -> Sound & Video -> Sound Recorder.

I worked on this for weeks with a Toshiba 650. This was so easy when all along it was in the Ubuntu Software Center. As soon as I added the GNOME ALSA MIXER it worked perfected!
Thank You Sir! :)

---

### Post by windozh8ter on 2011-03-19
Lidex, I'm hoping you can help. So far you've helped me get my sound back, my ubuntu desktop, and even my microphone to work...well, sometimes...I've tried I think all of your suggestions. I can boot up (Ubuntu 10.10 amd64, kernel[FONT=monospace] [/FONT]2.6.35-28-generic) and test my microphone and it works. I can even place a test call in Skype and it works. However, as soon as I place a video call in Skype, the microphone immediately stops working. After it stops in Skype, it also stops working for all other programs. Here is a link to the results of the alsa-project.org script: [http://bit.ly/f9OXP8](http://bit.ly/f9OXP8). Any suggestions would be very much appreciated. Thanks!

---

### Post by lidex on 2011-03-20
> **windozh8ter said:**
> Lidex, I'm hoping you can help. So far you've helped me get my sound back, my ubuntu desktop, and even my microphone to work...well, sometimes...I've tried I think all of your suggestions. I can boot up (Ubuntu 10.10 amd64, kernel[FONT=monospace] [/FONT]2.6.35-28-generic) and test my microphone and it works. I can even place a test call in Skype and it works. However, as soon as I place a video call in Skype, the microphone immediately stops working. After it stops in Skype, it also stops working for all other programs. Here is a link to the results of the alsa-project.org script: [http://bit.ly/f9OXP8](http://bit.ly/f9OXP8). Any suggestions would be very much appreciated. Thanks!

My first thought is check your skype preferences and disable the option to allow skype to control levels. Reset your level in sound preferences.

---

### Post by windozh8ter on 2011-03-23
Sorry, Lidex, I couldn't try your suggestion right away (traveling). I gave it a shot, but it still doesn't work. The entire microphone thing just seems really flaky. One time I can do a successful Skype test call, the next time I can't. Sometimes my Preferences > Sound > Input options show that the microphone is receiving sound, sometimes not. I just don't know what to make of it. Do you think I might need to try a totally different sound driver?

---

### Post by lidex on 2011-03-23
> **windozh8ter said:**
> Sorry, Lidex, I couldn't try your suggestion right away (traveling). I gave it a shot, but it still doesn't work. The entire microphone thing just seems really flaky. One time I can do a successful Skype test call, the next time I can't. Sometimes my Preferences > Sound > Input options show that the microphone is receiving sound, sometimes not. I just don't know what to make of it. Do you think I might need to try a totally different sound driver?

No. Re-edit your alsa-base.conf file. Remove this line:
```
options snd-hda-intel model=dell-m4-1
```
Edit this line:
```
options snd-hda-intel model=hp-dv5
```
to look like this:
```
options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot.

Edit command:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by sammiev on 2011-03-23
May I add that after the last kernel update, I had to redo all over again with my mic. GL :)

---

### Post by windozh8ter on 2011-03-24
Thanks for the response, Lidex. I tried the latest suggestions (from post #45) and the result is that:

* Sound Preferences shows microphone input, 
* gnome alsamixer shows microphone volume up, 
* PulseAudio Volume Control shows volume up on microphone (and unmuted), but the level doesn't show any input
* Skype test call fails to received sound from microphone, so I didn't even bother trying a video call.

Here are the script results, just in case you need the new version: [http://bit.ly/i2w2gD](http://bit.ly/i2w2gD)

I see in another post of yours about Kubuntu 9.10 (see #6 at [http://ubuntuforums.org/showthread.php?p=9072172](http://ubuntuforums.org/showthread.php?p=9072172)) that you recommend enabling unsupported (backports) repo in "Software Sources" and installing the alsa modules. Is this something than can be done in Ubuntu 10.10 also?

---

### Post by lidex on 2011-03-24
> **windozh8ter said:**
> Thanks for the response, Lidex. I tried the latest suggestions (from post #45) and the result is that:

* Sound Preferences shows microphone input, 
* gnome alsamixer shows microphone volume up, 
* PulseAudio Volume Control shows volume up on microphone (and unmuted), but the level doesn't show any input
* Skype test call fails to received sound from microphone, so I didn't even bother trying a video call.

Here are the script results, just in case you need the new version: [http://bit.ly/i2w2gD](http://bit.ly/i2w2gD)

I see in another post of yours about Kubuntu 9.10 (see #6 at [http://ubuntuforums.org/showthread.php?p=9072172](http://ubuntuforums.org/showthread.php?p=9072172)) that you recommend enabling unsupported (backports) repo in "Software Sources" and installing the alsa modules. Is this something than can be done in Ubuntu 10.10 also?

You still have that 'auto' model in there and alsa is picking it up. Remove it and reboot.

---

### Post by windozh8ter on 2011-03-25
Thanks, Lidex. I got rid of the auto line (see [http://bit.ly/e6fUFf](http://bit.ly/e6fUFf)). I had to reboot twice in order to get any of the Sound Preferences to show input. Then I had a successful test call on Skype for a sound check, so I initiated a test video call. The other party reported me hearing me say, "hello?" and then there was no more sound. So I guess we made some progress, but the settings don't seem to be sticking. Have you ever seen this happen before?

---

### Post by DutchieR on 2011-03-29
> **dazeddezzy said:**
> thank you this worked for my issue.
Which Microphone did you use? I have Mic1, Mic2 and Linein

---

### Post by adduds on 2011-03-31
> **steve-o1983 said:**
> I had the same problem, especially with Skype.  After searching some forums, someone recommended installing Pulse Audio (you can find it in the Software Center "PulseAudio Volume Control").  Once installed, go to the Input Devices tab and put the front left on "Max" and the front right on "Silence".  That should solve the problem.  You will also have to go into Skype options - Sound Devices and make sure that the box is unchecked for "Allow Skype to automatically adjust my mixer levels."  That will throw it off every time.

that worked perfectly for me thanks very much for this post!!!

---

### Post by Peter_1984 on 2011-03-31
It might not be 100% related to Skype but I had a similar problem and saw some people mentioning that you have to change the connector in the sound settings.
Now I am a bit confused since that option simply does not exist on my laptop (using ubuntu 10.10 maverick meerkat).
Any ideas as to the reason of this?
thanks in advance from a complete ubuntu newbie.

---

### Post by adduds on 2011-03-31
did you try the post above yours? ie. mine that worked for me just go to software center and type pulse and follow his directions maybe that'll work

---

### Post by gladbagz on 2011-03-31
**Re: Need help in getting microphone to work.** 			
 			 			 		   		 		 		My integrated microphone will not work and I have tried every suggestion  on this thread and others I think.  My laptop is a Compaq Presario  V6000.  Here is the rest of my info.

# uname -a
Linux laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 26 2011 for kernel 2.6.35-28-generic (SMP).

# head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20549 (Venice)

My Alsa information is at [http://www.alsa-project.org/db/?f=53...4a6ed108b00b11]("http://www.alsa-project.org/db/?f=5321fd21901c3216d24a6b07f14a6ed108b00b11")

Help would be appreciated.  I just want to talk to my wife and children over skype while I am away.

---

### Post by lidex on 2011-03-31
> **windozh8ter said:**
> Thanks, Lidex. I got rid of the auto line (see [http://bit.ly/e6fUFf](http://bit.ly/e6fUFf)). I had to reboot twice in order to get any of the Sound Preferences to show input. Then I had a successful test call on Skype for a sound check, so I initiated a test video call. The other party reported me hearing me say, "hello?" and then there was no more sound. So I guess we made some progress, but the settings don't seem to be sticking. Have you ever seen this happen before?

Make sure you disable the preference in skype to allow it to control audio levels.

---

### Post by windozh8ter on 2011-03-31
Yes, that preference continues to be unchecked. I'm still having the same problem where the other party hears me say literally "hello" & then the microphone cuts out and stops working not only in skype, but in all programs. Once again, thank you, Lidex. I really appreciate your time, expertise & help with this.

---

### Post by Joliea on 2011-04-04
Hi,

My problem was that the input sound was muted on the sound preferences. Unchecked the mute and everything was fine. Left click the volume icon, go to sound preferences, go to the input tab and ensure mute is unchecked.

Joliea

---

### Post by lidex on 2011-04-04
> **windozh8ter said:**
> Yes, that preference continues to be unchecked. I'm still having the same problem where the other party hears me say literally "hello" & then the microphone cuts out and stops working not only in skype, but in all programs. Once again, thank you, Lidex. I really appreciate your time, expertise & help with this.

I want you to take a look at this thread as that problem mirrors yours:
[http://ubuntuforums.org/showthread.php?t=1719957](http://ubuntuforums.org/showthread.php?t=1719957)

---

### Post by windozh8ter on 2011-04-04
Lidex is my hero!

---

### Post by sohaan on 2011-04-10
Many many thanks....it also solved my problem.

---

### Post by iamgeniusrnti on 2011-11-11
Hey,

I know this is an old thread but I had the same problem on two different computers (my Kubuntu on a 64 bit PC and my Ubuntu 10.10 running on my Acer One), both with Pulse Audio.

I spent about a week tweaking on it and I fixed it. thru no help of anyone whatsoever.  While everyone had bright ideas that seemed to work for them, none worked for me.

Then a week later, I was poking around the skype forum and someone was using pavucontrol to adjust his stereo output.  So I did the standard sudo apt-get install pavucontrol.  Then I gave it a whirl and caught something evil.

On my Acer One:  If you run pavucontrol and go to input devices, it sees my microphone as a stereo input.  I noticed when I 'unlinked' the left/right channels and turned the RIGHT channel all the way DOWN, and the LEFT channel all the way up, the microphone instantly started working.  Skype fixed.  

On my Kubuntu PC:  Whenever Skype was up and running, pavucontrol detected Skype was trying to use the microphone jack for a source and not my Logitech webcam mic.  So I clicked on the button and changed the source over to webcam mic.  Problem was instantly fixed.

While the Ubuntu Linux Gods found this problem uninteresting, I hope this posting will one day help out another of us little people.

---

### Post by Finn bjerke on 2011-11-13
Man you put a lot of work into this. Congrats on your succes, nowadays its Ubuntu 11.10 most people use. The new Ubuntu works better with laptop microphones in general.  Have you tried Ubuntu 11.10?

---

### Post by iamgeniusrnti on 2011-11-13
> **Finn bjerke said:**
> Man you put a lot of work into this. Congrats on your succes, nowadays its Ubuntu 11.10 most people use. The new Ubuntu works better with laptop microphones in general.  Have you tried Ubuntu 11.10?

Thanks.  I am actually away right now.  I had to fix my home pc via cbc thru an ssh pipe on a Droid tablet.  My netbook is running Ubuntu Ultimate Edition.  As I understand it, I would need to do a fresh install.  An upgrade I think would break it.

---

### Post by iamgeniusrnti on 2011-11-13
*vnc

---

### Post by Finn bjerke on 2012-03-10
upgrade ubuntu to 11.10 and the problem is solved imn my case at least.

---

### Post by MrJason005 on 2012-05-18
Bloody skype. I hate it when it doesn't work!
But thanks to this guy, it works! Hooray!

---

### Post by Finn bjerke on 2012-05-18
Try Ubuntu 12.04 it works with different mics. Microsoft have bought Skype, now and then skype is not working, may I suggest google plus "hangout" as a good user freindly alternative ?

---

