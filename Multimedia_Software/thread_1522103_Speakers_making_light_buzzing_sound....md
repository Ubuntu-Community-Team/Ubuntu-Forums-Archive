---
title: "Speakers making light buzzing sound..."
date: 2010-07-01
forum: Multimedia Software
---

### Post by etdsbastar on 2010-07-01
Hello there,

My speakers are making continuous slight buzz sounds. I don't know why this is happening but when i am making my sound to mute all, the sound goes off. When I hear properly, it seems to be the sound of the hard-drive spinning sound, I couldn't under from where it is coming, its happening from past 4-5 days. 

Please help me...

---

### Post by .Gregory. on 2010-07-01
Just out of curiosity, are you using a laptop or a desktop?

---

### Post by ubudog on 2010-07-01
How high is your PCM set?

---

### Post by ijse on 2010-07-01
try to disable **mic **in the alsamixer

good luck~!

---

### Post by etdsbastar on 2010-07-02
> **ijse said:**
> try to disable **mic **in the alsamixer

good luck~!

disabled mic, and the sound suddenly went off, i don't know how? but i think the problem still persists somewhere else.

---

### Post by ubudog on 2010-07-02
Did you check the PCM?

---

### Post by etdsbastar on 2010-07-03
> **ubudog said:**
> Did you check the PCM?

I am a newbee regarding hardware controlling in ubuntu, will you please tell me how to check it?

I am using Jaunty 10.04, where to check the PCM?

---

### Post by ubudog on 2010-07-03
In 10.04, make sure that the volume is not over 100%.  You can check in the sound config.  (found in the panel)

---

### Post by ubudog on 2010-07-03
Don't know if it will work in 10.04, but it worked for me on 9.04 (the PCM was set too high)

---

### Post by etdsbastar on 2010-07-03
> **ubudog said:**
> In 10.04, make sure that the volume is not over 100%.  You can check in the sound config.  (found in the panel)

Please have a look at my screenshot, after this setting also it my speakers are buzzing with a very low continuous hard-drive spinning like sound. 

But, when I click on mute, the sound goes off.

---

### Post by ubudog on 2010-07-03
Hmm, the PCM isn't the problem.

---

### Post by etdsbastar on 2010-07-05
> **ubudog said:**
> Hmm, the PCM isn't the problem.

then please tell me what's the exact problem. and how to solve it.

---

### Post by lidex on 2010-07-06
> **etdsbastar said:**
> Please have a look at my screenshot, after this setting also it my speakers are buzzing with a very low continuous hard-drive spinning like sound. 

But, when I click on mute, the sound goes off.
What happens when you turn your 'Alert Volume' down to 50% and your 'Output Volume' up to 100%?

Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by etdsbastar on 2010-07-07
> **lidex said:**
> What happens when you turn your 'Alert Volume' down to 50% and your 'Output Volume' up to 100%?

Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

The sound lowered down a little bit, and i also installed alsamixer and done as per your instructions. Recently updated to kernel version 2.6.32-24

---

### Post by etdsbastar on 2010-07-16
still not got relief from weired sound problem... Is anyone there to help me please.

---

### Post by oldsoundguy on 2010-07-16
The question was asked before.  Is this a laptop setup or a desktop? (as there are lots of things a user can do to check on a desktop .. and virtually NOTHING on a laptop is user friendly.)
Also .. on that attachment .. turn the alert volume down to  about 50%  and set your output at 50%.  Then you don't have to crank your playback volume up as much .. will give you more flexibility.

---

### Post by etdsbastar on 2010-07-17
> **oldsoundguy said:**
> The question was asked before.  Is this a laptop setup or a desktop? (as there are lots of things a user can do to check on a desktop .. and virtually NOTHING on a laptop is user friendly.)
Also .. on that attachment .. turn the alert volume down to  about 50%  and set your output at 50%.  Then you don't have to crank your playback volume up as much .. will give you more flexibility.

Its my desktop system Compaq CORE2DUO SG3470IL 2 GB Memory with Internal Sound System (no external sound cards) The sound is coming occasionally, Yesterday I found one thing. I had VLC installed, I was watching a movie, with the movie sound, buzzing sound was also coming with very light pitch, when I closed VLC the sound had gone. Again after sometime the buzzing started, but this time VLC was closed.

---

### Post by oldsoundguy on 2010-07-17
> **etdsbastar said:**
> Its my desktop system Compaq CORE2DUO SG3470IL 2 GB Memory with Internal Sound System (no external sound cards) The sound is coming occasionally, Yesterday I found one thing. I had VLC installed, I was watching a movie, with the movie sound, buzzing sound was also coming with very light pitch, when I closed VLC the sound had gone. Again after sometime the buzzing started, but this time VLC was closed.

as a retired professional audio engineer .. the first thing I always check is all CORDS and connections (Including the internal sound card if you are using one).  Then I check the power supply for the speakers (the wall wart). In Linux MECHANICAL (wiring) problems are much more frequent than software issues.
UNPLUG your microphone if you are using one.  Even muted, a defective microphone that is plugged in can cause problems.
Try running no more than one audio program plus the default computer audio (the notifications/alarms) at one time .. sometimes that can cause issues.

See if this helps, if not, you MAY have a software conflict issue and some of the software experts will have to jump in.

But the rule of thumb .. if it is mechanical, check it first! (replace as needed)

---

### Post by lidex on 2010-07-17
> **oldsoundguy said:**
> as a retired professional audio engineer .. the first thing I always check is all CORDS and connections (Including the internal sound card if you are using one).  Then I check the power supply for the speakers (the wall wart). In Linux MECHANICAL (wiring) problems are much more frequent than software issues.
UNPLUG your microphone if you are using one.  Even muted, a defective microphone that is plugged in can cause problems.
Try running no more than one audio program plus the default computer audio (the notifications/alarms) at one time .. sometimes that can cause issues.

See if this helps, if not, you MAY have a software conflict issue and some of the software experts will have to jump in.

But the rule of thumb .. if it is mechanical, check it first! (replace as needed)

Sounds good to me. As a very smart man once said: "There ain't no gas in it."

---

### Post by etdsbastar on 2010-07-19
I had checked all the cords, I have mercury speakers 4.1, everything perfect now related to cords and wirings.

I have noticed one thing yesterday, the sound is coming occasionally, when the sound started, I made my master sound to 0 and then again raised it, the sound went off, I don't know whether it is going to come again or not.

---

### Post by lidex on 2010-07-19
Check your profile in sound preferences, the hardware tab. I was playing with mine, just to see what I could see, and some provided no sound and others had a variety of distortion/crackling, etc.

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> Check your profile in sound preferences, the hardware tab. I was playing with mine, just to see what I could see, and some provided no sound and others had a variety of distortion/crackling, etc.

Watch the screenshot. I have only one sound hardware.

---

### Post by Lucifer The Dark on 2010-07-19
Do you have a switched on Mobile Phone within about 10 feet of your pc? I find they cause strange noises to come out of my speakers.

---

### Post by lidex on 2010-07-19
Just the stereo duplex, eh? I don't think we looked at your hardware.
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by etdsbastar on 2010-07-19
Hello friend, below given are the outputs of the commands you have  asked. Copied and pasted as it is.

My system model is Compaq SG3470IL - 2 GB RAM with internal sound card.

**$ uname -a**
```
Linux shrinu-server 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
```**$ aplay -l**
```
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```**$ dpkg -l | grep "alsa"**
```
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
```[B]
$ head -n 1 /proc/asound/card*/codec#*[/B]
```
Codec: Realtek ALC662 rev1
```

---

### Post by ubudog on 2010-07-19
> **Lucifer The Dark said:**
> Do you have a switched on Mobile Phone within about 10 feet of your pc? I find they cause strange noises to come out of my speakers.

Yes, this happens to me too.

---

### Post by lidex on 2010-07-19
We need to eliminate config issues. Run these commands to remove old config files: Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by ubermunkey on 2010-07-19
hi,

Not trying to stop a on going diag of the issue. However, even though pulse controls audio from the icon in your panel, sometimes alsa doesnt get the event. You might look at what the PCM volume or MASTER volume is inside alsa byy running
```
~#alsamixer
```
If you have already done this please ignor ythis post. In my case, the intel integrated HDA chipset has not played nice with anything using pulse.

Have Fun!

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> We need to eliminate config issues. Run these commands to remove old config files: Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```**Logout/in.**

This would be ok to perform dear, Please tell me, because already I am in problem, if I use the above commands, are they be recreated after login logout.

---

### Post by lidex on 2010-07-19
> **etdsbastar said:**
> This would be ok to perform dear, Please tell me, because already I am in problem, if I use the above commands, are they be recreated after login logout.

Absolutely.

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> Absolutely.

ok then please wait... dont' go offline i am reverting you back within few minutes.

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> Absolutely.

Oops, the output is below:

```
$ **rm -r ~/.pulse ~/.asound***
rm: cannot remove `/home/(...)/.asound*': No such file or directory
```

---

### Post by lidex on 2010-07-19
That's fine. Did you logout/in?

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> That's fine. Did you logout/in?

no, because there was no such folder in it. no changes appeared.

---

### Post by lidex on 2010-07-19
It removed the ~/.pulse folder. The error message was for the other files that do not exist unless you had created them.

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> It removed the ~/.pulse folder. The error message was for the other files that do not exist unless you had created them.

yes restarted the machine, everything came back as normal now what to do dear.

---

### Post by lidex on 2010-07-19
Beat me to it. In reading over the thread I thought we should revisit the alert volume in sound preferences. Try muting that or turning all the way down and play some music. Result?

---

### Post by etdsbastar on 2010-07-19
> **lidex said:**
> Beat me to it. In reading over the thread I thought we should revisit the alert volume in sound preferences. Try muting that or turning all the way down and play some music. Result?

Alert volume totally down (muted), playing songs in VLC perfectly till now, the problem persists occasionally. So, thanks a lot helping me till date.... But, I will report to you within a couple of days lidex, if the problem persists again... so, not making the thread as solved right now... One more question, should I make the alert volume up 40% or let it be muted.

Thanks a lot again for you beautiful support...

Bye and take care...

---

### Post by etdsbastar on 2010-07-31
The sound again started friends, Its now been heard from the login screen itself. Its weird, I don't know what to do? Else everything is working fine except that low-pitch continuous piiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiii like sound...

---

### Post by lidex on 2010-07-31
Try gnome alsamixer. Mute - don't just turn down - any and all input sources you are not currently using. Also make sure your sound levels are not in the red.

---

### Post by etdsbastar on 2010-08-01
> **lidex said:**
> Try gnome alsamixer. Mute - don't just turn down - any and all input sources you are not currently using. Also make sure your sound levels are not in the red.

I used alsamixer. I had noticed one thing today, when the system was started i started hearing this sound from the login screen itself, after successful login I played VLC and a song in it, the sound gone amazingly... It is coming when the system is idle, i mean to say the sound device/drivers are idle, i think so.

---

### Post by lidex on 2010-08-01
It may be system sounds. Did we try disabling that already? If there is a mixer entry for 'beep' disable that.

---

### Post by etdsbastar on 2010-08-01
> **lidex said:**
> It may be system sounds. Did we try disabling that already? If there is a mixer entry for 'beep' disable that.

mixer entry for beep has already been disabled. Watch the screenshot.

---

### Post by etdsbastar on 2010-09-25
Thanks for the help everybody but from yesterday onwards, again my speakers started those annoying buzzing sound like zzzzzzzzzzzzzzzz.... (high pitch but very slow)...

---

### Post by etdsbastar on 2010-10-16
again the same problem started. What to do friends.

pulseaudio[1578]: ratelimit.c: 576 events suppressed

This is the error I am getting through the log files after the buzzing sound being started.

---

### Post by phredbull on 2010-10-16
I think the problem is because of your lo-quality integrated sound card. I too can hear my CPU/HD making noise through the speakers of my laptop, and the noise is more noticeable when plugged into good speakers. I'm afraid this is caused by electromagnetic interference leaking into cheap, unshielded components. You should make sure all cables are plugged in firmly, all ground leads are properly attached, and if possible, keep power leads separate from audio leads. But most likely, the only solution will be to get a better sound card.

---

### Post by ubudog on 2010-10-16
Also, your cell phone right next to your speakers could be causing interference.

---

### Post by etdsbastar on 2010-10-22
> **ubudog said:**
> Also, your cell phone right next to your speakers could be causing interference.

I thought the same thing too... But, removing the cell phone too; i am getting the same sound.

---

### Post by ubudog on 2010-10-22
> **etdsbastar said:**
> I thought the same thing too... But, removing the cell phone too; i am getting the same sound.

Anything else?  Ipod, MP3 Player, etc?

---

### Post by etdsbastar on 2010-12-28
After updating to Marverick,

I am still getting that weired sound occasionally. Please help anyone...

---

### Post by oshunluvr on 2011-01-09
This is kind of an old thread but I had this issue too.

In my case, lowering the volume on the CD channel removed the static/buzz.

---

### Post by etdsbastar on 2011-07-25
Still didn't got rid of the sound,,,, zzzzzzzzzzzzzzz like sound very light. it goes off when i make the master sound up and again down, for a specific amount of time and then again starts annoying me. 

One more thing my messages.log is completely filled with ratelimit.c suppression events.

Please help.

---

