---
title: "Skype: A tail of woe and rubbish software"
date: 2009-12-03
forum: Multimedia Software
---

### Post by Clang on 2009-12-03
I am running a fully updated 9.10. My company decided to purchase a skype worldwide year contract for a little over a £100. Since skype supported linux "out of the box" we thought everything would be fine and, foolishly, went ahead and bought the contract without testing the client on ubuntu. Big mistake.

Skype doesn't yet support 9.10 officially (if their deb names are anything to go by), so I went ahead and download the intrepid deb. Everything installed fine, but upon testing I found that there was a loooong audio lag when talking to my boss across the room. This problem did not exist on windows, and a little googling revealed it was possibly a pulseaudio problem. (threads here: [http://ubuntuforums.org/showthread.php?t=976850](http://ubuntuforums.org/showthread.php?t=976850) [http://forum.skype.com/index.php?showtopic=237601](http://forum.skype.com/index.php?showtopic=237601)).

There are many proposed fixes in these threads, from uninstalling pulseaudio (protip to skype: don't require your users to downgrade core OS systems to work with your product, fix your product), to changing the output devices in the skype settings. The latter seemed to work for many people, but for me and a few others there was no option to change from pulseaudio. oh no.

In one of the many threads I trawled (possibly in the ubuntuforums thread linked above) I found a link to skype-debian_2.0.0.72-1_i386.deb, which apparently fixed this problem. So I went ahead and downloaded it and lo and behold, I can now select different audio devices. After much tweaking and some strange problems with calls going straight to voice mail (fixed by simply reinstalling, go figure) skype finally works without a horrific lag.

To anyone having problems with skype audio lag who can't select any audio device other than pulseaudio in skype options, here is (hopefully) your answer: [http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb) (not sure on location of 64-bit version I'm afraid). Uninstall skype, reinstall using the above deb, and tweak your audio options (options->sound devices in skype) to use your preferred hardware. For me this was my logitech usb headset and I configured it as follows:

Sound In: Logitech G330 Headset (hw:Headset,0)
Sound Out: Logitech G330 Headset (plughw:Headset,0)
Ringing: Logitech G330 Headset (plughw:Headset,0)

(I also had to set my headset as the default output and input device in System->Preferences->Sound)

My success might be related to my particular hardware, I have no idea.

My advice to anyone who is considering using skype on ubuntu or any linux. DO NOT. We are getting shafted with a shitty client that doesn't have half the features of the windows equivalent, yet we pay the same for the service. Furthermore, there is no notice from skype that they

a) don't support a range of linux operating systems
b) don't provide the same feature set on linux clients.

Personally, I think it is deceitful to advertise support for linux without stating that the clients they do provide are severely crippled and not supported anywhere near as well as the windows equivalent.

The newest linux clients don't work with the newest versions of ubuntu, and to get skype working we have to use an even older, less feature rich client, that is probably missing security fixes and god knows what else. 

By continuing to use skype and just "dealing" with these problems we are effectively telling skype that we like taking it up the ***. I read on the skype forum that they have TWO people developing for linux, and a much larger team for windows. Do yourselves a favour and move away from skype and use one of the MANY alternative voip services that respect their linux users. Skype have no monopoly and do not offer anything unique, other than a large user base. I implore you, DO NOT USE SKYPE, or else your end up a bitter sysadmin angry at having wasted your day, like me :) I'll be using up my credit then moving away from skype.

Finally, if any of the skype linux devs read this, I'm not having a go at you personally.. I imagine it is very difficult implementing features at the same rate as the windows team, especially when they only have one platform to worry about and a much larger team. I am angry because I feel your company only provides token linux support, and that throwing a "beta" label onto the client is no substitute for clearly stating the limitations of the implementation.

---

### Post by the8thstar on 2009-12-03
I installed Medibuntu repos and thus installed Skype on my system. I am not experiencing any lag.

My version is 0.2.1.47

---

### Post by AlanR8 on 2009-12-03
No audio lag at all here on 9.10. Had some issues with video on this Sony for a while but now resolved......

That said, wouldn't pay for Skype.....

---

### Post by kelvin spratt on 2009-12-03
What a lot of utter rubbish I use skype on Parsix/Arch/ ubuntu/mint/fedora/ gnome, LXDE,KDE4 WM. with no problems at all.

---

### Post by Clang on 2009-12-03
> **kelvin spratt said:**
> What a lot of utter rubbish I use skype on Parsix/Arch/ ubuntu/mint/fedora/ gnome, LXDE,KDE4 WM. with no problems at all.

I'm glad you don't have problems. However I assure that my post is not "utter rubbish" and that I have spent a whole day trying to work around these problems. 

If you feel the need to defend the skype linux client go ahead, as a user of the client I would find it hard emphasize, but I would listen to your claims respectfully. I would appreciate it if you don't discredit my claims because you haven't had the same problem.

---

### Post by ZoiaGuyver on 2009-12-03
I've had similar problems to those mentioned actually, they are posted a lot :P

It doe's seem to be something to do with Skype's way of handling the pulseaudio though.. the problem doesnt seem to appear if you use Alsa or OSS. There are a lot of people that say about pulse audio, but other than a popping prob i get if i leave the settings untouched, i have no issues other than Skype :D

---

### Post by oldgit on 2009-12-03
If you install skype-static from the medibuntu repo you should have a much more pleasant experience.

---

### Post by egruber on 2010-01-08
I'm a bit of a Linux newbie.  How do I get find the skype version on the Medibuntu Repository?  I want to try it.  Thanks!!

---

### Post by bbdimitriu on 2010-03-03
> **egruber said:**
> I'm a bit of a Linux newbie.  How do I get find the skype version on the Medibuntu Repository?  I want to try it.  Thanks!!

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

