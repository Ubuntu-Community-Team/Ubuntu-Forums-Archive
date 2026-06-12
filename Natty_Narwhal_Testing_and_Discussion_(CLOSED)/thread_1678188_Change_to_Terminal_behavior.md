---
title: "Change to Terminal behavior?"
date: 2011-01-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-01-29
I think this happened in the past day or so. In Natty's Terminal, I can no longer select text and paste it with the "middle" mouse button (clicking the left and right mouse buttons of a two-button mouse, simultaneously).

To me, this is a serious bug. I have been using UNIX systems for many years (at least 25 years) and the middle button to paste behavior has always worked. until now on Natty.

Is this change by design or is it something I should file a bug report on?

Tim

---

### Post by Harry33 on 2011-01-30
> **ratcheer said:**
> I think this happened in the past day or so. In Natty's Terminal, I can no longer select text and paste it with the "middle" mouse button (clicking the left and right mouse buttons of a two-button mouse, simultaneously).

To me, this is a serious bug. I have been using UNIX systems for many years (at least 25 years) and the middle button to paste behavior has always worked. until now on Natty.

Is this change by design or is it something I should file a bug report on?

Tim

What xserver-xorg-input-evdev version are you using?

---

### Post by ratcheer on 2011-01-30
Sorry, I have been out with my family all day.

I am currently running xserver-xorg-input-evdev 1:2.6.0-1ubuntu1

Tim

---

### Post by ratcheer on 2011-01-30
I just upgraded it to version 1:2.6.0-1ubuntu2, but the behavior did not change.

Tim

---

### Post by Harry33 on 2011-01-31
> **ratcheer said:**
> I just upgraded it to version 1:2.6.0-1ubuntu2, but the behavior did not change.

Tim

Right,

This is an evdev issue, however, it does not seem to a bug, it is a new property.
Evdev default config has been changed so that the 3 button emulation is off by default.
(3 button emulation = the usage of left and right buttons together to produce middle button effect).

I have the impression that this was done from the evdev version 2.5.
Now, Natty had the version 2.3 before (where 3 button emulation was auto by default).

So, in order to enable this function, try putting these lines in your xorg.conf.

Section "InputClass"
    Identifier "middle button emulation class"
    MatchIsPointer "on"
    Option "Emulate3Buttons" "on"
EndSection

---

### Post by autark on 2011-01-31
> **Harry33 said:**
>  This is an evdev issue, however, it does not seem to a bug, it is a new property.
Evdev default config has been changed so that the 3 button emulation is off by default.
(3 button emulation = the usage of left and right buttons together to produce middle button effect).

This sounds like a bad decision, unless I hear some really convincing arguments. Many laptops don't have a middle mouse botton, so many users will be left scratching their heads. The xorg.conf solution sounds like a terrible work-around.

---

### Post by zika on 2011-01-31
I do not think it is evdev issue, it works on my machine, totally up-to-date...
I do not remember changing anything in that department. I remember it did not work for some time, yesterday or so...
I have Parcellite active, so, it might be that... But, I had it active, also, when it did not work...

---

### Post by ratcheer on 2011-01-31
> **Harry33 said:**
> Right,

....

So, in order to enable this function, try putting these lines in your xorg.conf.

Section "InputClass"
    Identifier "middle button emulation class"
    MatchIsPointer "on"
    Option "Emulate3Buttons" "on"
EndSection

That works. Boy, do you know a lot of stuff! Thank you very much.

I still may open a bug, just to let them know this is not appreciated.

Tim

---

### Post by ronacc on 2011-01-31
I'll confirm and me too that bug . When they want to change a longstanding NORMAL behavior of the very core of linux ( the terminal ) it should be atleast widely announced and preferably put out for open discussion beforehand .

---

### Post by Mr. Picklesworth on 2011-01-31
Are you using a mouse or a touchpad? If it's a mouse, I think this has been the case for a while; Emulate3Buttons doesn't kick in for those on its own. It probably will if the mouse only has two buttons; I don't have a two button mouse to test that on (other than my touchpad).
Is yours *actually* a two button mouse?

Here's a kind of vaguely related thing:
[http://www.robmeerman.co.uk/unix/xinput](http://www.robmeerman.co.uk/unix/xinput) (Scroll down to the 10.04 stuff).

You can look through your devices with *xinput --list*, look at a specific device with *xinput --list [device-id]*, and list properties for a device with *xinput --list-props [device-id]*.
From there, you can see the number of buttons the system thinks your mouse has, and you can see the value of &#8220;Evdev Middle Button Emulation,&#8221; which is equivalent to Emulate3Buttons.
If it's a value other than 2, it isn't enabled. (And I don't know what it means). If it's 1, it is enabled and you're doing it wrong. You can change it with:
xinput --set-int-prop [device-id] [property-id] 8 1

(Oh, there's also a nice little GUI tool called gpointing-device-settings, but xinput is fancier)

If the system has definitely misread your mouse and thinks it's totally different than what it is, that is something suited for a bug report. If you want 3 button emulation enabled in all cases, I'm going to scream and stomp off in a grouchy mood :b

---

### Post by ratcheer on 2011-01-31
> **ronacc said:**
> I'll confirm and me too that bug . When they want to change a longstanding NORMAL behavior of the very core of linux ( the terminal ) it should be atleast widely announced and preferably put out for open discussion beforehand .

Thank you. I opened bug 710762 "Middle mouse button no longer works".

Tim

---

### Post by ratcheer on 2011-01-31
> **Mr. Picklesworth said:**
> Are you using a mouse or a touchpad? If it's a mouse, I think this has been the case for a while; Emulate3Buttons doesn't kick in for those on its own. It probably will if the mouse only has two buttons; I don't have a two button mouse to test that on (other than my touchpad).
Is yours *actually* a two button mouse?



Yes, it is a two-button mouse. Clicking the left and right buttons at the same time is supposed to emulate the middle mouse button and result in the Paste action. Not only have I been doing this on many systems (Solaris, HP-UX, AIX, Ubuntu, Debian, and probably several others for many years) it still functions this way for me on my fully updated Ubuntu 10.10 Maverick installation. This is much quicker and simpler than having to stop to type a three-key combination Ctrl-Shift-v or bring up a pop-up menu twice to Copy and Paste.

IMHO, it is wrong to change this widely standardized behavior.

Tim

---

### Post by ronacc on 2011-01-31
> **ratcheer said:**
> Thank you. I opened bug 710762 "Middle mouse button no longer works".

Tim

done and done

---

### Post by zika on 2011-01-31
> **zika said:**
> I do not think it is evdev issue, it works on my machine, totally up-to-date...
I do not remember changing anything in that department. I remember it did not work for some time, yesterday or so...
I have Parcellite active, so, it might be that... But, I had it active, also, when it did not work...I think Parcellite masked this bug for me... You're right...

---

### Post by ratcheer on 2011-01-31
A preliminary response to my bug report indicates that it is indeed an intentional change from upstream. It further speculates that users who use right-click to paste are likely "power users" who will be "happy" to code the needed changes into their xorg.conf files.

I am not a power user nor am I happy with having to code a workaround to maintain behavior that has been standard in X11 for many years.

Tim

---

### Post by ronacc on 2011-01-31
another case of the dumbing down of Ubuntu that they swear they aren't doing.

---

### Post by Mr. Picklesworth on 2011-01-31
> **ronacc said:**
> another case of the dumbing down of Ubuntu that they swear they aren't doing.

I don't think that's a fair accusation. This is upstream trimming fat (which has indeed been going on for a while); it isn't Ubuntu's thing at all. It's across the ecosystem. Everyone shipping xinput-evdev 2.6 is going to have this. Same deal as the hard-coded ctrl alt backspace thing. (And like that one, this could always be a nice addition to the mouse preferences&#8230;)

I agree with you, it would be nice if the xorg folks were more vocal when considering user-facing changes, but then this is the case with a lot of stuff. Perhaps something worth bringing up with them; maybe they just need the right person to help with it, or the right communication channel.

It would be really cool if we had one distro-neutral pot where important (and widely adopted) upstreams could dump surveys and the like, and have some idea what segment of their user base is answering them. (And with a good design, like what Mozilla is doing for Firefox 4, maybe it could have decent coverage). I don't think we have that, unfortunately. Unless it's a big specification, it's usually the odd mailing list post and somebody making an educated guess.



For clarity, this has *absolutely nothing to do with what the middle mouse button does when pressed*, but the various modes of pressing the button. That still (should) do the same thing it always does. If I'm wrong about that, please yell. I edited the bug report's description to avoid confusion, but it could be me being confused.

I'm curious if this affects touchpads, or if those are special-cased in some way. Unfortunately, my live usb just killed itself and my other Natty is in a VM&#8230; so is anyone else able to check that? :)

Oh, and so people can find it easily: [Here is the bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762")

---

### Post by mc4man on 2011-01-31
> I'm curious if this affects touchpads, 
It works fine here on a touchpad w/ no change to xorg.conf

From the bugs i've been involved in that were judged to be an upstream issue unless there is some compelling reason ubuntu will not 'fix' the source.
Sometimes a configuration change that improves the situation can be pushed thru, though I doubt this is one of those cases.

---

### Post by ronacc on 2011-01-31
ok I'll retract my comment at least in this instance . but as a note I sometimes use the "click both to emulate middle " even whe using a 3 button mouse to avoid moving my index finger to the wheel and then back to the select button if I'm in a hurry , so I'll ad that section to my xorg.conf .

edit   the retraction does not include my statement that a little better notification would have been nice .afterall this wasn't a bug fix but a change to longstanding behavior regaurdless of where it originated .

---

