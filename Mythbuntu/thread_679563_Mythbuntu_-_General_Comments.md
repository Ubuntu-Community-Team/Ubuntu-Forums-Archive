---
title: "Mythbuntu - General Comments"
date: 2008-01-27
forum: Mythbuntu
---

### Post by Titus A Duxass on 2008-01-27
Here are some comments that I have following several installs and a couple of months usage. I will not call them bugs because I do not have the necessary skills to isolate bugs. But I do think it is necessary to highlight them.

1. During the install I set my language to English, Location to Berlin and Keyboard layout to German. But the Keyboard layout always remains stuck in the US layout.

Changing the layout and instructing the system not to use xorg (therefore allowing the possibility to change the layout) and deleting the US layout followed by adding the German layout works until a reboot which puts you back to square one.

2. Strange codec problems (see my other thread), mythbuntu sometimes refuses to play certain DVDs despite having all codecs installed. I have never experienced these failures before and I have used SuSE, Debain, and ubuntu (5.10 and upwards) for mythboxes.

3. Quitting from DVD playback in xine (pressing Q) does not work correctly. It requires two presses of Q which then leads you to the "Do you want to leave mythbuntu..." screen. I do not know if this is a problem with mythbuntu or xine.

4. DVDs can only be ejected by using the Eject Media option in the DVD menu. Using this produces a small on screen message saying "Failed to Eject ..." even though the media has been ejected.

In general the install process is now a no-brainer which is good.

---

### Post by stdPikachu on 2008-01-27
> **Titus A Duxass said:**
> 1. During the install I set my language to English, Location to Berlin and Keyboard layout to German. But the Keyboard layout always remains stuck in the US layout.

Changing the layout and instructing the system not to use xorg (therefore allowing the possibility to change the layout) and deleting the US layout followed by adding the German layout works until a reboot which puts you back to square one.

I ran into this one too (trying to use a GB keyboard) and it'd never remember my prefs either. Managed to get it to work by editing the current US config rather than deleting it and creating a new one - does need to be fixed though!

Haven't run into your other problems I'm afraid. First off, do you have libdvdcss2 installed? You're using xine for playback presumably? What video output option is it using?

Regarding quitting xine, I found the default lircrc's a bit b0rked for my setup so I decided to roll my own - might be worth you comparing what irw says about your remote with what you can see under `grep -B3 -A5 xine ~/.lircrc`.

---

### Post by superm1 on 2008-01-27
> **stdPikachu said:**
> I ran into this one too (trying to use a GB keyboard) and it'd never remember my prefs either. Managed to get it to work by editing the current US config rather than deleting it and creating a new one - does need to be fixed though!

Haven't run into your other problems I'm afraid. First off, do you have libdvdcss2 installed? You're using xine for playback presumably? What video output option is it using?

Regarding quitting xine, I found the default lircrc's a bit b0rked for my setup so I decided to roll my own - might be worth you comparing what irw says about your remote with what you can see under `grep -B3 -A5 xine ~/.lircrc`.
Are you folks installing the nvidia driver?  If so, can you try an install without doing that and seeing if it keeps your config?

---

### Post by Titus A Duxass on 2008-01-28
I seem to remember that the keyboard layout was screwed before I even enabled the Nvidia drivers. But I can try an install without, give me a couple of days. 

I've just bought another slimline case and am building another system based on Horny Heron. But I will be installing the old fashioned way and not using mythbuntu. Will this make a difference?

If you want I can do a quick install from mythbuntu first.

I have libdvdcss codecs installed and yes I am using xine for DVD playback.  Video output is S-Video to a 32" CRT TV.

How did you manage to edit the US config?

---

### Post by stdPikachu on 2008-01-28
Erm, now you mention it I can't remember how I edited the default US config; think I just unticked the "use X settings" option, selected us and hit the edit button to change it to gb. Failing that I ran across the config file in ~/.config somewhere that you can edit manually as a last resort; XFCE isn't my DE of choice (KDE for work, fluxbox for lightweight stuff like Myth) and I know very little about it at the moment. Ah yes, there we go, .config/xfce4/mcs_settings/keyboard.xml

Similarly, ran into this keymap problem before I swapped the nv driver for the nvidia one (couldn't login as after the first reboot as my password contained an @).

---

### Post by jmatienzo on 2008-01-28
Try setting your repeat option in your lircrc file to 0, I think you have the repeat option set too high,that is why you are getting multiple presses. In other words you prolly have the repeat set to 3,so when you press a button it's repeating 3 times, you really only need that for the volume buttons and maybe the Up,Down,Left,Right buttons.

---

### Post by Titus A Duxass on 2008-02-03
Back to the original topics.

The keyboard problem only occurs when you preselect another language (not English). The keyboard layout is correct (German in my case) when running from the CD. Reboot after the install process and the keyboard layout defaults to US, going into setting => Keyboard Setting => Layouts, shows that the layout is driven by X configuration.

Disable this and you can see the available layouts (in my case there is only US). 

I added the German layout and deleted the US layout, reboot and every thing is fine.

I do not think that the NVidia drivers have any influence on the layout.

---

