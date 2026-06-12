---
title: "Ubuntu upgrade to 11.04 errors"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nipunreddevil on 2011-03-13
I upgraded my Ubuntu 10.10 to 11.04 using update-manager -d
Now the Gnome Desktop isn't working properly.I see my desktop but thats it.Nothing else seems to work.No commands etc.Also i can't see any of the menu bars or even the panels containing them.Only right clicks are working.I also had Kubuntu installed which seeems to be working correctly apart from some little bug.I re installed compiz using Kubuntu.How can i get my Gnome Desktop environment running properly

---

### Post by Dutch70 on 2011-03-13
> **nipunreddevil said:**
> I upgraded my Ubuntu 10.10 to 11.04 using update-manager -d
Now the Gnome Desktop isn't working properly.I see my desktop but thats it.Nothing else seems to work.No commands etc.Also i can't see any of the menu bars or even the panels containing them.Only right clicks are working.I also had Kubuntu installed which seeems to be working correctly apart from some little bug.I re installed compiz using Kubuntu.**How can i get my Gnome Desktop environment running properly**

Re-install a stable version of Ubuntu/Kubuntu, not a development release.

If you really want to help out with a development release, by reporting bugs & such. 
Create a separate partition on your hard drive especially for that release or use a virtual machine or usb stick.

---

### Post by nipunreddevil on 2011-03-14
Would it be fine if i keep updating my system and i shall have it all working fine with the stable release expected soon.I can keep my work going on from Kubuntu anyways.

---

### Post by uRock on 2011-03-14
The final release is more than a month away and likely to break your system during updates. I recommend a fresh install of 10.04 or 10.10.

Moved to NNT&D

---

### Post by beew on 2011-03-14
Why are people in such a rush to upgrade if they are not testing?? Maverick is only 5 months old for heaven's sake. Do people really have such short attention span these days? :)

---

### Post by nipunreddevil on 2011-03-14
Ok.
An error message i get upon startup:

Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/orca/orca.py", line 2300, in main
    if environ_message:
UnboundLocalError: local variable 'environ_message' referenced before assignment

Maybe this could be of help to the developers

---

### Post by Dutch70 on 2011-03-14
> **nipunreddevil said:**
> Ok.
An error message i get upon startup:

Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/orca/orca.py", line 2300, in main
    if environ_message:
UnboundLocalError: local variable 'environ_message' referenced before assignment

Maybe this could be of help to the developers

Sure, if you filed a bug report.

---

### Post by sammiev on 2011-03-14
The update went very well for me. Then I started to play and the desktop went dead. I rebooted to find the same. I couldn't even send a error report. So I went back to 10.10 from a backup. Have a small error from the backup and still can not get anyone to help me with that error. Started to look at other lunix software to run as I think lunix is the way of the future. GL :)

---

### Post by nipunreddevil on 2011-03-14
> **uRock said:**
> The final release is more than a month away and likely to break your system during updates. I recommend a fresh install of 10.04 or 10.10.

Moved to NNT&D
What about updating only when the final release is available?That logically seems ok

---

### Post by Dutch70 on 2011-03-15
If you really want to try your luck with that, go for it. However bug reporting will be irrelevant to whatever the current daily build is, because it may have been fixed long before you report it. 

Also, no one will be able to help you when you have problems.

---

### Post by cariboo on 2011-03-15
This thread seems to have gotten off on the foot. To the op can you log into the Classic Desktop?

---

### Post by ve3tru on 2011-03-15
"Why are people in such a rush to upgrade if they are not testing"
I can't speak for others, but with 10.04 I had so many issues that were never resolved.Older versions seemed more stable but less polished and won't run my peripherals properly, It seems they only get fixed in a new disto. I had printers scanners webcams that wouldn't work right in older versions. To top if off I had a screen flicker in 10.04 that got so bad, after a while my computer would crash this made it unusable. I no longer have these problems but new ones that need to be resolved. The whole concept of LTS is a joke, I dont upgrade for more fluff but more functionality.

---

### Post by KegHead on 2011-03-15
Hi!

I'm using 11.04 as I write this memo.

When I double click on listen to music I'm sent to the internet-firefox.

Anyone else?

KegHead

---

### Post by ivanovnegro on 2011-03-15
> **ve3tru said:**
> "Why are people in such a rush to upgrade if they are not testing"
I can't speak for others, but with 10.04 I had so many issues that were never resolved.Older versions seemed more stable but less polished and won't run my peripherals properly, It seems they only get fixed in a new disto. I had printers scanners webcams that wouldn't work right in older versions. To top if off I had a screen flicker in 10.04 that got so bad, after a while my computer would crash this made it unusable. I no longer have these problems but new ones that need to be resolved. The whole concept of LTS is a joke, I dont upgrade for more fluff but more functionality.

I know exactly what you mean and this is the problem with Ubuntu and why I am not using the LTS versions. Always they are saying "use an LTS version for stability", I cannot agree with this statement because the LTS was also buggy.
Im sorting my problems out, somehow I can live with it but maybe try another distro.

---

### Post by KegHead on 2011-03-15
Hi!

Also something weird!

Tried to install chrome with no luck..I'm using an USB sick.

KegHead

---

### Post by savantelite on 2011-03-15
If this is a post about x no longer working from an update, subscribe me. Yesterday's Update killed compiz for me:(

---

### Post by beew on 2011-03-15
> **ve3tru said:**
> "Why are people in such a rush to upgrade if they are not testing"
I can't speak for others, but with 10.04 I had so many issues that were never resolved.Older versions seemed more stable but less polished and won't run my peripherals properly, It seems they only get fixed in a new disto. I had printers scanners webcams that wouldn't work right in older versions. To top if off I had a screen flicker in 10.04 that got so bad, after a while my computer would crash this made it unusable. I no longer have these problems but new ones that need to be resolved. The whole concept of LTS is a joke, I dont upgrade for more fluff but more functionality.

You have a point, but rememberl this is an ALPHA release! It still ndoesn't make sense to me that anyone would upgrade his main work OS from a stable release to an alpha just because a printer or a scanner doesn't work. 11.04 crashes every 30 minutes or so on my machine (it used to be every 5 minutes so things have gotten better) Is it so urgent that one cannot wait a month for the official release to upgrade?

P.S. By "stable release" I meant something that has been officially released for general use, not necessarily a LTS.  10.10 is not a LTS but it is the latest stable release, it is barely 5 month old! You don't get any argument with me re LTS. I find 10.10 working better on all my machines than 10.04, though 10.04 is quite good too.

---

### Post by nipunreddevil on 2011-03-20
> **cariboo907 said:**
> This thread seems to have gotten off on the foot. To the op can you log into the Classic Desktop?

The classic desktop works fine.odd crashes but nothing major.The ubuntu desktop still doesn't work properly.

---

### Post by kansasnoob on 2011-03-20
The standard Natty Ubuntu desktop doesn't work at all well with my Intel Atom w/Intel graphics, but Compiz never has worked very well with it.

I've had much better luck using either the Classic Desktop w/o effects or Unity-2d with the ppa:

[https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily](https://launchpad.net/~unity-2d-team/+archive/unity-2d-daily)

Somewhat OT, but I'd go absolutely crazy if I didn't multi-boot for testing purposes. I know this is major overkill but:

[ATTACH]186608[/ATTACH]

Currently three of those OS's are in need of repair or replacement but I needn't worry or hurry. If I get the least bit tired or frustrated I just boot something I know works :D

Lubuntu Natty is looking particularly promising.

---

### Post by nipunreddevil on 2011-04-17
A strange issue.
After the upgrade

/proc/acpi/video is missing


How do i fix that?

With the partial upgrades the stability is improving,but it's clearly not to upgrade on alpha releases.

---

### Post by nipunreddevil on 2011-04-17
Moreover VLC behaves strangely.The sound produced is a trouble to the ears.The other music players wotk fine

---

