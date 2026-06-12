---
title: "Unmute sound doesn't work"
date: 2012-06-11
forum: Multimedia Software
---

### Post by maitteo on 2012-06-11
Hi guys!
I'm a newbie of Lubuntu 12.04 LTS , and i can't unmute sound with a shortcut key (the default keybind is "XF86AudioMute") : the sound is muted, but when i'm pressing AudioMute it can't unmute, and i must go in alsamixer GUI to unmute it.

I have googled, mainly the problem is in the rc.xml file, in the keybindings declarations, but I have seen the code to toggle the mute/unmute and it is is right!

I'll attend a your answer!

Thank you in advance , and sorry for my bad English! :p

---

### Post by maitteo on 2012-06-12
Up! :P

---

### Post by maitteo on 2012-06-13
Up! Is it a bug?
If it is , i'll going on Launchpad...

---

### Post by Kremlin on 2012-09-23
I'm also experiencing the same problem. Pressing the mute key (Fn-F8 on my Acer netbook) does mute the sound, but it will not unmute when pressed again. Instead, I have to use the Volume Control applet by the clock to unmute.

---

### Post by lyovushka on 2012-10-16
Had the same problem. Here is the solution. Edit ~/.config/openbox/lubuntu-rc.xml file. Find the section

    <keybind key="XF86AudioMute">
      <action name="Execute">
          <command>amixer -q sset Master toggle</command>
      </action>
    </keybind>

and modify the command to 

amixer -D pulse -q sset Master toggle

Restart openbox.

Hope this helps.

---

### Post by Kevin McCready on 2012-10-20
the suggested solution just disabled the mute button altogether.
At least I can still use the volume buttons.

---

### Post by daugl on 2012-12-20
Just stumbled over this thread and wanted to let you know that lyovushka's solution worked. :D
Of course you need to insert the -D pulse option into the key bindings for raising and lowering the volume of you want them to unmute.
I'm using Lubuntu 12.04 on MSI MS-168A.

---

