---
title: "[SOLVED] Is there a quicker way to mute/unmute the headphones?"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by YAOMTC on 2007-11-08
I often switch between using my headphones and using my speakers. This becomes quite tedious, as I don't want to have to unplug/plug in my headphones all the time, and I have to open up the full Volume Control to the Switches tab every time. Might there be some faster way to do it?

*Possibilities...*
It'd be nice if I could have a panel item that would serve as a mute/unmute button for the headphones, or even an option under the volume control's context menu. Might there be some keyboard shortcut I don't know about, maybe? Or is it possible to make one if there isn't?

---

### Post by YAOMTC on 2007-11-09
Time to move it up.

---

### Post by YAOMTC on 2007-11-12
.

---

### Post by YAOMTC on 2007-11-12
.

---

### Post by YAOMTC on 2007-11-13
.

---

### Post by tgalati4 on 2007-11-13
Do you have a "headphone sense switch" in your volume control Edit--> Preferences?

You could by a cheap audo A/B switcher from Radio Shack or an electronics surplus store.  

You can also get an old stereo receiver and set it up for your speakers and then use the headphone jack from that.  That's what I do.  I simply switch the A/B/Off switch when I want speakers, headphones, or both.

You could write a cheesy script using amixer and put an icon on the desktop that points to it.

>amixer scontrols

That will get you started.

---

### Post by YAOMTC on 2007-11-13
No "headphone sense switch", and... I don't have room for a switcher. Even the top of my computer's taken up by stuff. D:

I think the script would be the best thing, but... I don't know how.
```
Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Front Mic',0
Simple mixer control 'Line',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'IEC958',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'Input Source',0
Simple mixer control 'Input Source',1
```

---

### Post by YAOMTC on 2007-11-14
.

---

### Post by Whiffle on 2007-11-14
You could do something like this:

```

#\bin\bash
       aumix -Wq |grep -q 100
        if [ $? == 0 ]; then
          aumix -W mute
       else
          aumix -W 100
        fi

```

It toggles the Headphone setting on mine between 100 and mute.  It requires aumix which you should be able to find with apt-get or synaptic.  You might have to do some fiddling to figure out which channel it is, but once you do you could put it in a script, chmod +x it, and then run it from a keyboard shortcut.

---

### Post by YAOMTC on 2007-11-14
I can't get this to work. Sorry, I'm just not familiar with making scripts at all. Could you go into that a bit further? Like, I got aumix-gtk (should I have gotten the regular one without the GUI that I can't figure out how to use?), and... well, I have no idea what I'm doing. Not with aumix, not with chmod... x_x

---

### Post by YAOMTC on 2007-11-15
.

---

### Post by bluepowder7 on 2007-11-16
i have and use a 4-channel headphone distribution amplifier (pro audio / studio type gear), into which i plug my headphones (uses 1 channel for that) as well as my powered speakers (uses another channel for them).  it's easy to control an overall level, plus individual levels, and mute each of the 4 channels independently.  by the way, each "channel" is a stereo path.  the unit is only 1U high [that's 1.75"] and does double-duty as a platform to raise my LCD monitor up a bit.  if you have an LCD, just place it on top of the headphone amp.  if you have a heavy CRT, well then that's another issue.

also, mine has direct inputs on each channel, so you could quickly plug in an iPod on the front using a simple cable and route that signal to the speakers (heck, you can even mix the ratio of computer-to-iPod so you can pipe in your own tunes while playing Quake or whatever)

you might find smaller 2-channel types, which would be enough for headphones+speakers.

---

### Post by YAOMTC on 2007-11-16
Eheh... I don't really have money to spend on that, unless it's just a few dollars at Radio Shack or something. Otherwise, a script is the way to go, but I don't know how to modify the one written up previously to make it work. (See bottom post on page 1.)

---

### Post by Whiffle on 2007-11-16
I havn't forgotten about you, i just have zero free time right now to explain it out.  If you like, you can install aumix and play around with it in the terminal, its got a pretty good help function and man page.  

As far as the script i wrote goes, it might just work without modification.  Copy it into a text file, save it as "something.sh", run  "chmod +x something.sh", and then do ./something.sh and it just might do the trick.

---

### Post by YAOMTC on 2007-11-16
Hm. I can't seem to be able to do aumix -q (query all channels and print their settings). Every time I get:
SOUND_MIXER_READ_DEVMASK

I also get that when I try to run the script, except it repeats once. Anybody think they know what's wrong there?

---

### Post by Whiffle on 2007-11-17
Hmm, i get that on my ubuntu box too, but not on my slackware one.  From a quick search it looks like a bug in the package, you could maybe try getting a debian or feisty package and installing that, or compile it from source.  Or, wait for it to be fixed.

---

### Post by YAOMTC on 2007-11-17
Uh... *what* package, exactly? :?

---

### Post by YAOMTC on 2007-11-19
.

---

### Post by Whiffle on 2007-11-19
[http://packages.ubuntu.com/feisty/sound/aumix](http://packages.ubuntu.com/feisty/sound/aumix)

---

### Post by YAOMTC on 2007-11-19
Nice! Thanks, Whiffle! Now, let's see about making this script work...

---

### Post by YAOMTC on 2007-11-19
It works! Nice!

Thanks, Whiffle! [img]http://img.photobucket.com/albums/v256/attack_mayo/little/thumbsup.png[/img]

But... it seems that when I run it through the terminal, it works perfectly, but when I double-click the file itself and click "Run In Terminal" or just "Run", it can only unmute the headphones, not mute them. Any idea what might be wrong here? I'd like to make this a panel launcher (as of course that'd be faster than typing ./m.sh in a terminal), but this only seems to be an unmute button at this point. :?

---

### Post by jis on 2008-03-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/aumix/+bug/145805](https://bugs.launchpad.net/ubuntu/+source/aumix/+bug/145805) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **YAOMTC said:**
> Hm. I can't seem to be able to do aumix -q (query all channels and print their settings). Every time I get:
SOUND_MIXER_READ_DEVMASK


It's a bug. Add gutsy-proposed repository and update your aumix, if you want to use it.

Anyway, I have used amixer; by it you can toggle (i.e. mute/unmute) a control.

---

### Post by YAOMTC on 2008-03-02
> **jis said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/aumix/+bug/145805](https://bugs.launchpad.net/ubuntu/+source/aumix/+bug/145805) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

It's a bug. Add gutsy-proposed repository and update your aumix, if you want to use it.

Anyway, I have used amixer; by it you can toggle (i.e. mute/unmute) a control.I had that working quite a while ago. I guess I should have updated this thread I forgot about!

---

