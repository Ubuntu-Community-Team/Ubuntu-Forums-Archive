---
title: "Sound died for no apparent reason. Tried many solutions. Still no go."
date: 2010-03-14
forum: Multimedia Software
---

### Post by inspired on 2010-03-14
Hi folks,
Well, I guess the good news is that I've had sound working perfectly for over a year on this trusty laptop.

About a week ago audio stopped working.
Since fiddling around with it this weekend, I have discovered that headphones work.
In Pulse the sound meters and application monitors all show what they should. It "appears" all is working perfectly, but nothing comes out of the speakers.

[LIST]
[*]I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)  -- I note this has left me with an inconsistant ALSA installation. Take a look at this info on pastebin: [http://pastebin.ca/1840579](http://pastebin.ca/1840579)
The UTILITIES have the older version number.
[*]I also did a reinstall of Pulseaudio.
[*]I made sure my user name was in all the audio and pulse related groups.
[*] I've worked through SOME of the stuff here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[/LIST]

I am not sure what else to do. It looks like sound is fine in Pulseaudio monitor, etc., as I said.

Is there something obvious I am not switching, clicking, setting, etc.?

I'd love some help on this. Keen to get my laptop speakers going again, as I'd rather not wear earphones all day.

Thanks,

Jonathan

---

### Post by Yellow Pasque on 2010-03-14
Run the ALSA upgrade script again (first with -c, then with the -i option). If the alsa-utils section fails, post the output.

What model laptop do you have?

---

### Post by inspired on 2010-03-15
Thanks. I ran it three times... -d -c -i
I have the log from each. Is there any advantage to running it again, or just post the logs I already have?
Cheers,
Jonathan

---

### Post by Yellow Pasque on 2010-03-15
No, that's fine. Post the logs from the -c and -i sessions.

---

### Post by inspired on 2010-03-15
> **Temüjin said:**
> No, that's fine. Post the logs from the -c and -i sessions.
I appreciate your help.
I didn't realise that the content of the /tmp folder is automatically cleared out by the OS. So the logs are not there. So I am running it again. Took ages last time... so will post the logs here once complete.

The laptop is an HP Compaq NX7010.
Sound typically worked great once I got Pulseaudio correctly set up and understood its quirks. I let a few things update in the past week or two, and it may be that audio died as a result of that... but not sure exactly.

logs coming soon.

---

### Post by inspired on 2010-03-15
Here are the logs. Too big for forum limits, so put them on pastebin

Compile log: [http://pastebin.ca/1841766](http://pastebin.ca/1841766)
Install log: [http://pastebin.ca/1841770](http://pastebin.ca/1841770)

The status of the audio is no worse or better since doing this ALSA update. I gather the install failed... at least in the install log it says it failed to configure the Utils.

---

### Post by Yellow Pasque on 2010-03-16
> checking panel.h usability... no

checking panel.h presence... no

checking for panel.h... no

configure: error: required curses helper header not found


Do you have the libncurses5-dev and libncursesw5-dev packages installed?

---

### Post by inspired on 2010-03-18
> **Temüjin said:**
> Do you have the libncurses5-dev and libncursesw5-dev packages installed?

Hi there.
They were not installed, so I installed them and then reran the -c and -i versions of the script.

Logs posted on pastbin:
Compile log: [http://pastebin.ca/1844346](http://pastebin.ca/1844346)
Install log: [http://pastebin.ca/1844343](http://pastebin.ca/1844343)

Looks like there were even greater issues / errors. Not sure what to make of them though.

**UPDATE**: Taking a look at the results of the alsa-info script, there is still an older version of alsa-utils installed.

---

### Post by inspired on 2010-03-23
Hi folks,
I've still had no luck getting my sound (to built in laptop speakers) back. Any ideas? Would love to sort this out.

Regards,
Jonathan

---

### Post by lidex on 2010-03-23
Try this. In a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the bottom of the file:
```
options snd-intel8x0 ac97_quirk=3
``` 
save and reboot. Recheck your mixer levels.

---

### Post by inspired on 2010-03-24
Thanks folks.
Well, today it came right. No idea why.
I fiddled around with a few switches etc., and then unticked the "Headphone Jack Sense" switch. I had previously tested that (numerous times, in my hunt to resolve this) but it made no difference. When this issue arose I had to check that switch in order to get sound from AT LEAST the headphones, as opposed to no sound at all. Now, switching that off means both the speakers and the headphones are functional. Perhaps (partially successful) upgrade to the ALSA system resolved something but it only became obvious with the "Headphone Jack Sense" switched off.

@LIDEX - should I still make that change you suggested, or just leave things as they are now that it is working again?

Thanks folks for your help. Something worked. Glad to have sound back. Headphones are such uncomfortable things when used long term... and my partner will be glad I can now hear her when she talks to me and I am on the computer!! :D

---

### Post by lidex on 2010-03-24
> @LIDEX - should I still make that change you suggested, or just leave things as they are now that it is working again?

If it works leave well enough alone. If you find sound gone again after a reboot or it's just not persistent then go ahead with it.

---

