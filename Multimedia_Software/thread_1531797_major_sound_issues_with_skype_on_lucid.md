---
title: "major sound issues with skype on lucid"
date: 2010-07-15
forum: Multimedia Software
---

### Post by ethos_dacapo on 2010-07-15
I have upgraded to lucid on my netbook successfully with skype working great but i have done two brand new installs on two different computers and in both cases the audio coming to and from skype is totally unusable. I had to reinstall windows in order to have a computer dedicated to my skype phone system. This is not desirable at all so i would like to get this figured out. I checked the settings in the pulse daemon and default files and they were the same as on my netbook which works great. I'm using the same usb adapter with kb2skype so it shouldn't have anything to do with the hardware. When i make a call from the clean ubuntu install it cuts out every other second and the mic is so far delayed its unusable.

---

### Post by ethos_dacapo on 2010-07-16
The last several times i've posted a thread asking for help on these forums i get no response at all. What gives people????

---

### Post by lidex on 2010-07-17
There are any number of skype threads on these forums. Have you looked at them and what have you tried so far?
[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")
[http://blogs.skype.com/linux/2009/09/some_explanations.html]("http://blogs.skype.com/linux/2009/09/some_explanations.html")
[https://help.ubuntu.com/community/SkypeTroubleshooting]("https://help.ubuntu.com/community/SkypeTroubleshooting")

---

### Post by ethos_dacapo on 2010-07-17
> **lidex said:**
> There are any number of skype threads on these forums. Have you looked at them and what have you tried so far?
[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")
[http://blogs.skype.com/linux/2009/09/some_explanations.html]("http://blogs.skype.com/linux/2009/09/some_explanations.html")
[https://help.ubuntu.com/community/SkypeTroubleshooting]("https://help.ubuntu.com/community/SkypeTroubleshooting")

Thanks for your reply. I've spent several hours on several different occasions trying to find the solution to this problem. The closest i got was editing a few lines in the daemon file, this helped improved sound quality for me somewhat but not nearly as good as it sounds on windows on the same machine or on my netbook running ubuntu 10.04 from upgrade. The mic audio was still unusable. I can't believe no one else has posted anything regarding this issue... still running windows for my main skype line until a solution can be found. I'll be working on it more this coming week.

---

### Post by lidex on 2010-07-17
How is the mic audio outside of skype?

Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**.

---

### Post by ethos_dacapo on 2010-07-18
> **lidex said:**
> How is the mic audio outside of skype?

Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**.

Sound works fine otherwise just not with skype. I just installed the above package but it didn't make any difference even after reboot. To help clarify, when the call starts the audio of skype dialing out is fine its only once i begin receiving audio from the echo service or someone begins talking on the other end that i get a crunch effect every second or so. When i use the mic it has the same crunching effect where there is alot of distortion and words get smashed together. Thanks your help btw!

---

### Post by lidex on 2010-07-18
OK. But have you tried the mic in another program to see if it works properly there?

---

### Post by ethos_dacapo on 2010-07-18
> **lidex said:**
> OK. But have you tried the mic in another program to see if it works properly there?

Yes, sound is perfect in and out using the same hardware. I'm playing with settings in the daemon file right now but its not doing much good at all... Any suggestions my friend?

---

### Post by ethos_dacapo on 2010-07-18
Ok i've made some progress. The sound is near perfect coming in but the mic still sounds choppy. I enabled these settings in my daemon file ```
high-priority = yes
nice-level = 3
```

I used 3 as was recommended on some forum i was on a few days ago. This got the audio on my end sounding great but when i test the mic it still chops it up at some points its lagging at others it skips ahead. Any ideas??

---

### Post by lidex on 2010-07-18
Have you unchecked the option in skype to control mixer levels?

---

### Post by ethos_dacapo on 2010-07-18
> **lidex said:**
> Have you unchecked the option in skype to control mixer levels?

Never thought to try it as the volume levels are fine. Its like the mic isn't getting buffered correctly because the words get ran together and even cut off at times. I just tried unchecking that option with no difference. Any way i can increase the mic buffer or do you have any other ideas of what could be causing this? Its happened on two different computers from fresh installs of lucid.

---

### Post by lidex on 2010-07-18
This happens on two different computers? Now that is weird. Is this using the same mic?
Also have a thorough read of this page:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")
Make sure to read the section 'Restore Default Configurations'

---

### Post by ethos_dacapo on 2010-07-18
> **lidex said:**
> This happens on two different computers? Now that is weird. Is this using the same mic?

Yes, two completely different systems with clean installs of lucid. Both using the same usb telnet box. This box works fine with my netbook running lucid from an upgrade but i want to use my netbook as its intended not tied down with usb devices especially when i have a couple desktops just sitting around collecting dust.

edit: i should also note that the telnet box was just recently purchased so i never done anything on the netbook to make it work in the past it just worked out of the box. This has to be something between pulse and skype.

---

### Post by Linuxforall on 2010-07-18
My audio was generally noisy with Ubuntu, it got worse after skype, this on a old Yamaha card. I would hear constant cracking noise with sound, other programs like Smplyer, VLC and others would also start cracking after opening up skype and the only way to get rid of that would be to reboot. I installed Kubuntu which doesn't use Pulse and all my noise went away, sound is flawless and my love for KDE is back again after 1999 with SUSE.

---

### Post by ethos_dacapo on 2010-07-18
> **Linuxforall said:**
> My audio was generally noisy with Ubuntu, it got worse after skype, this on a old Yamaha card. I would hear constant cracking noise with sound, other programs like Smplyer, VLC and others would also start cracking after opening up skype and the only way to get rid of that would be to reboot. I installed Kubuntu which doesn't use Pulse and all my noise went away, sound is flawless and my love for KDE is back again after 1999 with SUSE.

Thank you! I've used the netbook remix and studio editions but never kubuntu, i guess nows time to give it a shot. I would have never thought to do so otherwise.

This still isn't the answer i was looking for but if it works i'll settle for it, especially on a computer who's only  function is to run skype.

---

### Post by lidex on 2010-07-18
If your only object is to run skype, you can remove pulseaudio. Others have had that plight.
[http://art.ubuntuforums.org/showpost.php?p=9202054&postcount=133]("http://art.ubuntuforums.org/showpost.php?p=9202054&postcount=133")

Or use lubuntu:
[https://wiki.ubuntu.com/Lubuntu]("https://wiki.ubuntu.com/Lubuntu")

---

### Post by ethos_dacapo on 2010-07-18
> **lidex said:**
> If your only object is to run skype, you can remove pulseaudio. Others have had that plight.
[http://art.ubuntuforums.org/showpost.php?p=9202054&postcount=133]("http://art.ubuntuforums.org/showpost.php?p=9202054&postcount=133")

Or use lubuntu:
[https://wiki.ubuntu.com/Lubuntu]("https://wiki.ubuntu.com/Lubuntu")

I tried removing pulseaudio in the past and it only made things worse. Installed kubuntu and set it as default vs. gdm but now i can't remote back in to it. I'll have to dig out the monitor and accessories later and see what gives.

---

### Post by Linuxforall on 2010-07-19
> **ethos_dacapo said:**
> I tried removing pulseaudio in the past and it only made things worse. Installed kubuntu and set it as default vs. gdm but now i can't remote back in to it. I'll have to dig out the monitor and accessories later and see what gives.

Has Kubuntu solved your sound issue?

---

### Post by ethos_dacapo on 2010-07-19
> **Linuxforall said:**
> Has Kubuntu solved your sound issue?

It may have but since i can't get remote access i won't know until i have time to hook up a monitor and keyboard etc... I  will let you know either way asap.

---

### Post by ethos_dacapo on 2010-07-19
> **ethos_dacapo said:**
> Thank you! I've used the netbook remix and studio editions but never kubuntu, i guess nows time to give it a shot. I would have never thought to do so otherwise.

This still isn't the answer i was looking for but if it works i'll settle for it, especially on a computer who's only  function is to run skype.

Ok i do not like kde at all. I installed it and it and switched to a kde session, but guess what? Skype was still defaulting to pulseaudio server under sound option with no chance of changing it. I previously tried uninstalling pulseaudio altogether but then i got no sound at all from the usb device. This is turning into a whole lot of bs just to be able to use a simple app. Maybe i should just stick with windows.

---

### Post by ethos_dacapo on 2010-07-19
Ok i uninstalled kde and pulseaudio. This time i also opened the alsamixer and adjusted the volume, vola! I have working incoming and outgoing sound finally. Now if i could just get the caller id to work :P Thanks everyone for your help!

---

