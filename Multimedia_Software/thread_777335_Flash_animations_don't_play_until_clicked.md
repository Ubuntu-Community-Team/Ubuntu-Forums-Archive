---
title: "Flash animations don't play until clicked?"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Mugsy323 on 2008-05-01
This is odd.

Any website I visit with embedded Flash (aka Shockwave) animations in it, all I get is a box with a "(>)" (Play) button in it where the animation should be. I must then click it to get the animation/video/etc to run.

There MUST be an "auto play" setting somewhere that I'm missing.

Details: 64bit Ubuntu 8.04 with Firefox. Flash plugin was installed automatically (via Firefox's plugin finder) with the first site I visited that contained a Flash animation in it.

Any ideas? Is this a glitch particular to Ubu64? I don't remember having this problem with 32bit Ubu 7.10.

---

### Post by deadgobby on 2008-05-01
MMM it sounds like flash blocker is installed. However before I say flash blocker is installed. Do you see this on the attachment?

---

### Post by whitefort on 2008-05-01
I have the same problem since I installed Hardy/Thunderbird 3.  It was never an issue in Gutsy.

I've no idea how to fix it, but for what it's worth, it's definitely not unique to 64-bit Ubuntu, because that's not what I'm using.

An additional issue is that in a lot of sites that used to work with Gutsy/Thunderbird 2, (for example, BBC sites), only gibberish appears when I click that little play button.

---

### Post by styphon on 2008-05-03
I have this problem as well. I had installed Ubuntu within Windows when it came out and everything was ok. Now I've done a fresh install direct onto the HDD rather than within windows and this happens. Also, when I click the play, within mini-clip some games wont work that did work before, and within youtube the files are laggy. The graphics aren't always displaying properly either.

I'm running 8.04 i386. Any help would be appreciated.

---

### Post by styphon on 2008-05-03
Found the culprit. For some reason the libswfdec-0.6-90 package was installed. Go into Synaptic Package Manager, search for that file and completely remove it. This has solved my problem completely.

---

### Post by legendnz on 2008-05-09
Thanks Styphon, this worked for me too. Having to click on the button was getting annoying. Thanks again..

---

### Post by styphon on 2008-05-09
Glad to have helped :).

---

### Post by hodenkat on 2008-05-09
cool!

it worked for me too!
wasn't a problem in 7.10... I just let it have the plugins it said it needed and it messed it up. This thread should be a stickie thread since most people are going make the same mistake!:mad:

---

