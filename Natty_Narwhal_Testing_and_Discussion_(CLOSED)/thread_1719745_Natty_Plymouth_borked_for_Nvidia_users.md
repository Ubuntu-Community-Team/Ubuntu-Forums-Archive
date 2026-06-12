---
title: "Natty Plymouth borked for Nvidia users"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by perrantrevan on 2011-04-02
Before upgrading from Maverick I was able to have a smooth and good-looking boot-up thanks to this guide: -

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

Now Plymouth only shows during shutdown. I just get  black screen and a cursor during startup (GRUB2-->X)

I think this is happening because the resolutions available to GRUB2 have changed (vbeinfo in grub console). Before you could choose 24 bit colour. Now you can only choose 8 or 32 bit colour which doesn't match the 24bit colour required to have a decent Plymouth boot (sudo hwinfo --framebuffer).

Can anyone else confirm this? Is there a workaround?

---

### Post by Quackers on 2011-04-02
With the beta release I'm getting a black screen with a flashing cursor top left for a good few seconds. I then get a magenta screen with "ubuntu 11.04" on it, but it only appears for about half a second. The laptop then boots.
Something similar happened occasionally with the alpha release on my system.
Maybe a Plymouth update will solve it.

---

### Post by VinDSL on 2011-04-02
Same here!

I spent a LOT of time making Plymouth look good during the 10.10 Maverick tests.

I was shocked to discover that Plymouth, on 11.04 Natty Alpha, looked identical to my tweaked 10.10 install!

Since the last round of updates, the Plymouth in Natty Beta looks just as bad as the Maverick Alpha.  LoL!

Oh, well, I suppose this shall pass, as well.

If not, I know how to fix it...  ;)

---

### Post by VinDSL on 2011-04-02
> **perrantrevan said:**
> Before upgrading from Maverick I was able to have a smooth and good-looking boot-up thanks to this guide: -

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

Can anyone else confirm this? Is there a workaround?
Took me a while to find it, but...

Here's the guide I used, to fix Maverick:   [http://ubuntuforums.org/showthread.php?t=1558174](http://ubuntuforums.org/showthread.php?t=1558174)

If you try this, make sure to read the whole thread, before attempting it.

If I remember correctly, you only have one shot at it!

If you miss up, it'll bone your install...  ;)

---

### Post by Harry33 on 2011-04-02
The real issue is with the newest grub2 packages (version 1.99~rc1-8ubuntu1).
This has been done there:
 > 
*Rewrite hwmatch.lua in C.  Drop lua grub-extras module.


So if you want the Plymouth back (Nvidia proprietary driver users) or if you want Plymouth to work correctly (NVidia, ATI, Intel open source driver users) you have to options:

1. Go and reverse the latest changes to the file /etc/grub.d/10_linux
You have there these three lines:

```

if [ \${recordfail} != 1 ]; then
  if hwmatch \${prefix}/gfxblacklist.txt 3; then
    if [ \${match} = 0 ]; then

```

Remove the second line only and put the following three lines there instead.
They were there in the previous version (1.99~rc1-6ubuntu1).
So that it (all five lines) will look like this:

```

if [ \${recordfail} != 1 ]; then
  set matches_file=\${prefix}/gfxblacklist.txt
  set class_match=3
  if lua \${prefix}/hwmatch.lua; then
    if [ \${match} = 0 ]; then

```


2. This does not correct anything, but you can alternatively
downgrade to the previous grub2 (version version 1.99~rc1-6ubuntu1).
You may have to uninstall the current grub2 first if downgrading does not prompt you to change the file /etc/grub.d/10_linux.

And you have the Plymouth back.
This is obviously a regression (bug).

---

### Post by Quackers on 2011-04-02
At the prompt when updating, I chose to keep the current version of /etc/grub.d/10_linux, so I would have expected no changes to take place in that respect. Evidently I was wrong :-)

---

### Post by Harry33 on 2011-04-02
> **Quackers said:**
> At the prompt when updating, I chose to keep the current version of /etc/grub.d/10_linux, so I would have expected no changes to take place in that respect. Evidently I was wrong :-)

That should have happened, but for me the upgrade process did not ask nor prompt me anything, because I hadn't modified that 10_linux file before.

---

### Post by Quackers on 2011-04-02
Ah yes, I had made changes to that file earlier, which is why I got the prompt.
Maybe there'll be an update :-)

---

### Post by Harry33 on 2011-04-02
> **Quackers said:**
> Ah yes, I had made changes to that file earlier, which is why I got the prompt.
Maybe there'll be an update :-)

Well I certainly hope so.
Please test my "three line addition - one line deletion" or actually reverting to the previous 10_linux.

---

### Post by perrantrevan on 2011-04-02
Thanks for all the responses!


Harry33. The previous grub-pc package wasn't available to download so I went for your first option.

Now, my grub background image remains visible until X starts but there is still no Plymouth until shutdown (so no progress indicator or fsck info etc.

So, it's an improvement but not as good as what I had with Maverick :-(

Thanks a lot. I really hope this get's fixed by some update but I'm not holding my breath!

---

### Post by Harry33 on 2011-04-02
> **perrantrevan said:**
> Thanks for all the responses!


Harry33. The previous grub-pc package wasn't available to download so I went for your first option.

Now, my grub background image remains visible until X starts but there is still no Plymouth until shutdown (so no progress indicator or fsck info etc.

So, it's an improvement but not as good as what I had with Maverick :-(

Thanks a lot. I really hope this get's fixed by some update but I'm not holding my breath!

Perrantrevan, the Plymouth in Natty has never been as good as it was in Maverick with open source graphics drivers.

---

### Post by perrantrevan on 2011-04-02
> **Harry33 said:**
> Perrantrevan, the Plymouth in Natty has never been as good as it was in Maverick with open source graphics drivers.


Well, maybe one of the devs might comment if I file a bug, but I'm not sure if the change is with grub-pc, plymouth, or the vbe graphics driver.

I can't be sure but I think it worked in Maverick because the grub-vbe driver @1280x800-24 matched the frame buffer resolution in plymouth. Now, only 32bit is possible for grub.

Here's hoping that this time next year I'll be able to use nouveau rather than the proprietary drivers!

---

### Post by VinDSL on 2011-04-02
> **Harry33 said:**
> The real issue is with the newest grub2 [...]

1. Go and reverse the latest changes to the file /etc/grub.d/10_linux
You have there these three lines:

```

if [ \${recordfail} != 1 ]; then
  if hwmatch \${prefix}/gfxblacklist.txt 3; then
    if [ \${match} = 0 ]; then

```

Remove the second line only and put the following three lines there instead.
They were there in the previous version (1.99~rc1-6ubuntu1).
So that it (all five lines) will look like this:

```

if [ \${recordfail} != 1 ]; then
  set matches_file=\${prefix}/gfxblacklist.txt
  set class_match=3
  if lua \${prefix}/hwmatch.lua; then
    if [ \${match} = 0 ]; then

```

Whoa!  THANK YOU, HARRY!  =D>

That worked a treat, in more ways than you might imagine.

Not only did your hack restore my beautiful Plymouth, but...

I checked my boot chart:


[INDENT][IMG]http://vindsl.com/images/vindsl-zuul-natty-20110402-4.png[/IMG]
[/INDENT]


**[COLOR="Red"]THE FIRST[/COLOR]** 18-second boot time, in the history of this machine -- under **[COLOR="red"]ANY[/COLOR]** OS!!!

OK, I'm gonna go calm myself down...

Whew!  That was exciting!  :D


**EDIT**


BTW, I did a...

```

sudo update-grub

```

...after the hack.

I don't know if this was necessary, but it never hurts, yes?

---

### Post by Quackers on 2011-04-02
Hmm, no fix for me, but I did get these errors while trying to save the edited file
```
nattybeta@nattybeta-VGN-AR51SU:~$ gksu gedit /etc/grub.d/10_linux

(gedit:3891): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.5JMITV': No such file or directory

(gedit:3891): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3891): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7QS7SV': No such file or directory

(gedit:3891): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
nattybeta@nattybeta-VGN-AR51SU:~$ gksu gedit /etc/grub.d/10_linux

(gedit:3909): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.O3GJTV': No such file or directory

(gedit:3909): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3909): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VSSATV': No such file or directory

(gedit:3909): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

---

### Post by VinDSL on 2011-04-02
Sorry for being rudimentary, but...

You are editing/saving that file under elevated privileges, yes?

It looks like you are, but I see many permission problems in the error dialog.

Hrm...

Interesting!

**EDIT**

If you'll pardon the pun, the .xbel extension rings a (ahem) bel.

That's what proggies, like Opera use, to store bookmarks, e.g. an attempt at standardization.

I'm *thinking* those errors might signal a gedit problem... perhaps a bug.

---

### Post by Quackers on 2011-04-02
I had this problem with an earlier version of 11.04. I can't remember what fixed it now :-(  I'll have a look through my old posts, but I had a feeling that an update solved it. I used the same method to update 40_custom just yesterday with no problems at all.
All of the errors above are regarding saving the file to various xbel files that don't exist or can't be created.
They only appear at the "quit file" stage - in other words after saving the file.

---

### Post by VinDSL on 2011-04-02
LoL!  I might as well burn off some nervous energy, since Harry33's hack turned me manic...

When I edit files that require elevated privileges, I use Nautilus.

Nautilus has an "Open as administrator" option, if you install the 'nautilus-gksu' package in Synaptic.

Just saying...

---

### Post by Quackers on 2011-04-02
All ideas are welcome :-)
I'm recalling something about it being a gedit problem.
Here's the old post - it caused quite a stir :-)
I have just employed the fix from post #25 and gedit has now stopped giving the errors posted earlier. File is saved and while you're reading this I'll be rebooting to view any changes to Plymouth :-)
[http://ubuntuforums.org/showthread.php?t=1631433](http://ubuntuforums.org/showthread.php?t=1631433)

---

### Post by VinDSL on 2011-04-02
> **Quackers said:**
> I have just employed the fix from post #25 and gedit has now stopped giving the errors posted earlier. File is saved and while you're reading this I'll be rebooting to view any changes to Plymouth :-)
[http://ubuntuforums.org/showthread.php?t=1631433](http://ubuntuforums.org/showthread.php?t=1631433)
Hrm...

I just checked, and that folder already exists on my install.


[INDENT][IMG]http://vindsl.com/images/vindsl-nautilus-2-apr-2011.png[/IMG][/INDENT]


Some proggie, or another, must have automagically created it for me.

---

### Post by Quackers on 2011-04-02
It should be created automatically iirc, but as you can see it wasn't. Anyway it's all fixed for the moment and Plymouth is back :-)
Only 45 second boot for me though - but that's normal for my machine :-)
I've been re-arranging my grubs! nattybeta is now in control and I'm in the middle of editing 40_custom now so that I can boot all my live cd .iso's from it :-)
It's all good fun!

---

### Post by VinDSL on 2011-04-02
> **Quackers said:**
> It's all good fun!
Agreed!  And, informative...

Every cloud has a silver lining!

I didn't realize Lua was being utilized in the core OS, until I read Harry's post.

That, alone, made my day!  :)

---

### Post by Quackers on 2011-04-02
Me neither! I didn't realise I had it! Maybe I can use it in conky now :-)
I'll look into it, though that's a different learning curve :wink:

---

### Post by Harry33 on 2011-04-11
This issue has been fixed now with the latest grub update (1.99~rc1-12ubuntu1)
This will change the file /etc/grub.d/10_linux too.
Now gfxpayload works and is set on for those graphics cards,
that are listed in the new package grub-gfxpayload-lists.
This is also a new dependency.

---

