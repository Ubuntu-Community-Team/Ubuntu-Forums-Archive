---
title: "Kernel LIRC keyboard configuration"
date: 2012-10-24
forum: Mythbuntu
---

### Post by KjetilK on 2012-10-24
I've struggled a lot with getting the keyboard setup of LIRC right after an upgrade. I have a MCE Remote [the second one here](http://www.mythtv.org/wiki/MCE_Remote#Media_Center_Remotes). Some keys actually work in MythTV, so I know that something is right. Moreover, with [FONT="Courier New"]xev[/FONT] I see that many more keys emit XF86-events, e.g. XF86AudioRecord, etc. 

So, for the first iteration, it would be nice to just make the XF86-events work, since I have a Cideko Air keyboard that emit those too. I know that I can do that in MythTV by editing keys, but that sounds rather cumbersome. Can I add the XF86 keys by editing a file somehow?

Next, I want the rest of the keys to work. That includes the OK button and the colored buttons... I suppose that I need something between e.g. KEY_OK and a real key event, but I can't find a lot of documentation here for the newfangled kernel stuff, so I'm not getting anywhere...

Can anybody please advice me on any of these?

---

### Post by alien878 on 2012-10-25
Yeah, the documentation is rather lacking....

Anyway, you might want to look at ir-keymap.  You may see more key events then make it to X such as the OK.  Supposedly he keymaps can also be modified with this command, but I've never figured it out.  I didn't look too hard as for me it was easier to re-program the remote.

---

### Post by KjetilK on 2012-10-25
> **alien878 said:**
> Yeah, the documentation is rather lacking....

Anyway, you might want to look at ir-keymap. 

ir-keymap? Do you mean ir-keytable? I did play around with ir-keytable a bit, and I got signal for every key on my remote. I haven't heard about ir-keymap however.

Basically, I have tried all different paths I found in [this guide](http://forum.xbmc.org/showthread.php?tid=104541), but none made any difference. In all cases, I ultimately have the same keys working and the same keys not working. 

That's why I'm thinking I'm approaching this on the wrong level. The IR remote is probably working, it is probably sending all the events, but something isn't generating the right keyboard events for me based on the IR events. Anyway, I'm just thinking loud, I don't really know if this is correct. Nevertheless, your help is appreciated!

---

### Post by alien878 on 2012-10-26
Yes.  I meant ir-keytable.  Oops :)

If ir-keytable -t works, you should be able to create a custom keymap table so all keys work (grep the existing config files with the working scancodes on your remote should identify the original config to use as a basis).

That link has a good description (better than the ones I found at the time).  Note that I never remapped the keys as I had a programmable remote and enough working keys on the original to fill it.

---

### Post by KjetilK on 2012-11-02
I returned to this problem now that the Wife Acceptance Factor falls to an alarmingly low level... :(

So, it appears that the keymaps are OK. All scancodes have a corresponding key code. I can run ir-keytable -t from my workstation over SSH to my myth box (running both frontend and backend) while MythTV is running. If I hit the UP key while in a menu, Myth is doing the right thing, and ir-keytable -t outputs
```

1351895064.055623: event MSC: scancode = 800f041e
1351895064.055633: event key down: KEY_UP (0x0067)
1351895064.055636: event sync
1351895064.189626: event MSC: scancode = 800f041e
1351895064.189630: event sync
1351895064.439075: event key up: KEY_UP (0x0067)
1351895064.439079: event sync
1351895391.539372: event MSC: scancode = 800f0423

```
while if I hit the Back key on the remote, Myth does absolutely nothing, but ir-keytable -t outputs
```

1351895391.539381: event key down: KEY_EXIT (0x00ae)
1351895391.539383: event sync
1351895391.645358: event MSC: scancode = 800f0423
1351895391.645361: event sync
1351895391.778377: event MSC: scancode = 800f0423
1351895391.778381: event sync
1351895392.027055: event key up: KEY_EXIT (0x00ae)
1351895392.027059: event sync

```

So, the scancode seems OK, the keytable seems OK... It has to go wrong at a higher level than that, right? What remains? ](*,)

---

### Post by Lester_Burnham on 2012-11-03
Hi,

Are you still using lirc also? Or pure devinput?
You need to find the devinput config for your different apps. It might be in lircrc or a different file.
If using lirc also, lircd.conf should give you a hint. If not, I'm not really sure where to look.
If using lirc, the configs may be in ./lirc/mythtv.

I'd just be guessing the config file does not match the button name.

Lester

---

### Post by jksj on 2012-11-03
The best guide to this seems to be [http://linhes.org/projects/linhes/wiki/Architecture_and_Customization.]("http://linhes.org/projects/linhes/wiki/Architecture_and_Customization")
I too am trying to use ir_keytable for my remote. I think that unlike with lirc the only mappping file is the keytable managed by ir_keytable. There is no application specific mapping as there is with lirc. 
 If you have to use **devinput** then you will likely not be able to use your normal lircd.conf file but instead you will need to use the standard **devinput** version of lircd.conf which is in "/usr/share/lirc/remotes/devinput/lircd.conf.devinput".
 So install lirc to set up devinput conf file then remove lirc.
  ```
 sudo apt-get purge lirc
 sudo apt-get install lirc
 Install lirc choose Linux input layer and choose /dev/input/by-path/....your remote.
  sudo apt-get remove lirc
 sudo ir-keytable -w /etc/rc_keymaps/tbs6920 –load keymap for your remote
```

---

### Post by Lester_Burnham on 2012-11-03
Hi,

I have had it working before with devinput and lirc. Using an MCE remote and keyboard.
[http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/](http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/)
Beware of the bold tags in the code. Forum formatting messed it up.

The whole remote thing in mythtv does my head in at the moment in this transitional period. Unless you're doing it weekly :)

I book marked that page. Thanks for the info.

Lester

---

### Post by KjetilK on 2012-11-03
> **Lester_Burnham said:**
> Hi,

Are you still using lirc also? Or pure devinput?
You need to find the devinput config for your different apps. It might be in lircrc or a different file.

I've uninstalled lirc, so I hope I'm using pure devinput. :-) And, yeah, I haven't looked into any further devinput config, but perhaps I'll find that in the mythbuntu-control-centre?

---

### Post by Lester_Burnham on 2012-11-03
Maybe. There is a devinput remote option in there.
I'm about to setup a test system again to play soon.

Lester

---

### Post by KjetilK on 2012-11-03
> **jksj said:**
> The best guide to this seems to be [http://linhes.org/projects/linhes/wiki/Architecture_and_Customization.]("http://linhes.org/projects/linhes/wiki/Architecture_and_Customization")


OK, nice, I'll look into that!

> **jksj said:**
> 
 
 If you have to use **devinput** then you will likely not be able to use your normal lircd.conf file but instead you will need to use the standard **devinput** version of lircd.conf which is in "/usr/share/lirc/remotes/devinput/lircd.conf.devinput".

Right, that's what I thought I did already. I might not have done it right, though.

However, now I tried to use mythbuntu-control-center to use "Linux /dev/input/eventX", which reinstalled lirc and seems to have configured MCEUSB again... That makes all keys work, but throws me back to where I really started: Some keys sends two keypresses... However, now I see that it is just the keys that worked previously that sends two keypresses... So, perhaps I could disable some of the kernel-stuff, perhaps that'd be easier. Possibly just blacklist some modules or something?

---

### Post by Lester_Burnham on 2012-11-03
> **KjetilK said:**
> That makes all keys work, but throws me back to where I really started: Some keys sends two keypresses... However, now I see that it is just the keys that worked previously that sends two keypresses... So, perhaps I could disable some of the kernel-stuff, perhaps that'd be easier. Possibly just blacklist some modules or something?

Two key presses in mythtv or IRW when testing?

Lester

---

### Post by KjetilK on 2012-11-04
> **Lester_Burnham said:**
> Two key presses in mythtv or IRW when testing?


Both, it seems.

---

### Post by Lester_Burnham on 2012-11-05
Hi,

See if it is the bug mentioned here [http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)

---------------
Please note that there is a bug which causes duplicate mappings to be generated. This can cause remote input to be processed twice. For instance if you press "down" and the menu selection moves down two items or if you press "pause" and the recording immediately pauses and then starts playing again. For more information please see the the Ubuntu Launchpad bug 779835.
--------------

Lester

---

### Post by alien878 on 2012-11-05
Hi KjetilK,

The back key is recognised as KEY_EXIT according to ir-keytable.  I suspect your issue now is that myth is not responding to that key.

To fix that, go into the front end setup and find the key mappings section.  In there, find the action you want KEY_EXIT to map to and add the new key to it.  To be sure that the correct key is added, use your remote and press the back key to enter it.

Cheers,

Allen

---

### Post by KjetilK on 2012-11-22
> **Lester_Burnham said:**
> Hi,

See if it is the bug mentioned here [http://www.mythtv.org/wiki/LIRC](http://www.mythtv.org/wiki/LIRC)


Actually, this gave me the hint I needed. :-)

I just needed 
```
 
echo lirc > /sys/class/rc/rc0/protocols 

```
in my /etc/rc.local

I'm still astonished it was *that* simple :-)

---

### Post by operat0r on 2012-12-02
I had issues after update: noting in my blacklist for remote stuff ... I just did  rm -Rf /usr/share/lirc/remotes/mceusb /etc/lirc apt-get purge lirc apt-get install lirc  I guess I had the confs wrong or something .. its working now so hope a reboot does not break it ..

---

