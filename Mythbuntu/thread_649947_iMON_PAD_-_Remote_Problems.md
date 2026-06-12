---
title: "iMON PAD - Remote Problems"
date: 2007-12-25
forum: Mythbuntu
---

### Post by JeepFreak on 2007-12-25
I'm trying to get my remote (iMON PAD) working on my new Mythbuntu 7.10 install.  I configured the remote during setup and didn't get any errors.

The problem is... only a few keys about half the buttons are recognized in Myth.  I am testing them by going to the 'Edit Keys' section in Setup.  I'm then attempting to bind certain buttons to certain actions.  I'm only doing it this way so that I can see what buttons are recognized, instead of wondering if they just don't have an action associated with them.

Anyway... these are the keys that *are* recognized in Myth:
Record
Play
Pause
Rewind
Enter
Mute
Ch +/-
Vol +/-
#'s 0-9

So, I ran IRW... all keys work *except*:
Power
App. Exit
The pad
My DVD
Menu

What the heck???  Where do I start?

Here are my unaltered files:
[SIZE="4"]**~/.mythtv/lircrc**[/SIZE]
[PHP]
begin
    remote = iMON-PAD
    prog = mythtv
    button = 7
    config = 7
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Right
    config = Right
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Mute
    config = |
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 1
    config = 1
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Down
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 0
    config = 0
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Pause
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Menu
    config = M
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 6
    config = 6
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 2
    config = 2
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Ch-
    config = Down
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Ch+
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Rewind
    config = <
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Play
    config = P
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Vol-
    config = [
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Stop
    config = Escape
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Vol+
    config = ]
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 5
    config = 5
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 4
    config = 4
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Enter
    config = Return
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Up
    config = Up
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Record
    config = R
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 9
    config = 9
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 3
    config = 3
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Enter
    config = Enter
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = 8
    config = 8
    repeat = 0
    delay = 0
end

begin
    remote = iMON-PAD
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

[/PHP]

[SIZE="4"]**/etc/lirc/lircd.conf**[/SIZE]
[PHP]#
# this config file was automatically generated
# using lirc-0.7.1pre2(imon) on Tue Mar  1 23:15:44 2005
#
# contributed by Venky Raju
#
# brand:                       iMON-New
# model no. of remote control: iMON-PAD
# devices being controlled by this remote:
#

begin remote

  name     iMON-PAD
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          235965
  min_repeat      1
  toggle_bit      0


      begin codes
          AppExit                  0x288195B7
          Record                   0x298115B7
          Play                     0x2A8115B7
          SlowMotion               0x29B195B7
          Rewind                   0x2A8195B7
          Pause                    0x2A9115B7
          FastForward              0x2B8115B7
          PrevChapter              0x2B9115B7
          Stop                     0x2B9715B7
          NextChapter              0x298195B7
          Esc                      0x2BB715B7
          Eject                    0x299395B7
          AppLauncher              0x29B715B7
          MultiMon                 0x2AB195B7
          TaskSwitcher             0x2A9395B7
          Mute                     0x2B9595B7
          Vol+                     0x28A395B7
          Vol-                     0x28A595B7
          Ch+                      0x289395B7
          Ch-                      0x288795B7
          Timer                    0x2B8395B7
          1                        0x28B595B7
          2                        0x2BB195B7
          3                        0x28B195B7
          4                        0x2A8595B7
          5                        0x299595B7
          6                        0x2AA595B7
          7                        0x2B9395B7
          8                        0x2A8515B7
          9                        0x2AA115B7
          0                        0x2BA595B7
          ShiftTab                 0x28B515B7
          Tab                      0x29A115B7
          MyMovie                  0x2B8515B7
          MyMusic                  0x299195B7
          MyPhoto                  0x2BA115B7
          MyTV                     0x28A515B7
          Bookmark                 0x288515B7
          Thumbnail                0x2AB715B7
          AspectRatio              0x29A595B7
          FullScreen               0x2AA395B7
          MyDVD                    0x29A295B7
          Menu                     0x2BA385B7
          Caption                  0x298595B7
          Language                 0x2B8595B7
          MouseKeyboard            0x299115B7
          SelectSpace              0x2A9315B7
          MouseMenu                0x28B715B7
          MouseRightClick          0x688481B7
          Enter                    0x28A195B7
          MouseLeftClick           0x688301B7
          WindowsKey               0x2B8195B7
          Backspace                0x28A115B7
# Corrin added
	  Space                    0x2B9B15F7
          Up                       0xEB53F9B7
          Left                     0x6ABAFFBF
          Down                     0x6F9ECBB7
          Right                    0x69A281B7

      end codes

end remote 

#
# this config file was automatically generated
# using lirc-0.8.0(userspace) on Tue Oct 17 22:45:11 2006
#
# contributed by 
#
# brand:                       Antec Fusion Wheel
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  Antec_Fusion_Wheel
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  16
  post_data      0xFF
  gap          131971
  min_repeat      1
  toggle_bit      0


      begin codes
          CCW                      0x0100
          CW                       0x0001
      end codes

end remote

[/PHP]

[SIZE="4"]**/etc/lirc/hardware.conf**[/SIZE]
[PHP]# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON PAD IR/VFD"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_imon"

# Default configuration files for your hardware if any
LIRCD_CONF="imon/lircd.conf.imon-pad"
LIRCMD_CONF=""
[/PHP]
[B]
Any help is appreciated!
Thank you,
Billy[/B]

---

### Post by erland on 2007-12-31
I think you need to recompile lirc with the pad2keys patch to get the pad navigation to work. Without this patch all my keys work with irw besides the pad and power.

However, the ~/.mythtv/lircrc doesn't contain all the keys so you won't be able to use them all with MythTV with the default configuration. To make the keys work in MythTV, you will have to edit this lircrc file.

It should contain an entries like this
```

begin
    remote = iMON-PAD
    prog = mythtv
    button = Caption
    config = T
    repeat = 0
    delay = 0
end

```

Where the button value "Caption" is the text you see in irw when a button is pressed and the config value "T" is the keyboard shortcut in MythTV. You will find the MythTV keyboard shortcuts available for example here:
[http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm](http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm)

---

### Post by JeepFreak on 2008-01-01
Thank you very much for the reply.

As far as the pad goes... I really want it to act in place of the arrow keys (on the keyboard), not control the mouse pointer.  Should I still go the route of the patch?

The link with the keyboard shortcuts is very helpful... Thank you.  I will work on adding more configurations.  I thought, at first, that I had button configured in my ~/.mythtv/lircrc file that were _not_ working in Myth... well, I *do*... but they are the keys that are also not working in irw.

Anybody know why certain buttons are not working in irw?  

Thanks!!
Billy

---

### Post by erland on 2008-01-01
> **JeepFreak said:**
> 
As far as the pad goes... I really want it to act in place of the arrow keys (on the keyboard), not control the mouse pointer.  Should I still go the route of the patch?I haven't tried it myself, but I think the purpose of the patch is to convert the pad to standard arrow keys.

> **JeepFreak said:**
> 
Anybody know why certain buttons are not working in irw?  

Assuming both mythfrontend and lirc has been shutdown, you can run:

sudo mode2 -d /dev/lirc0
(Where /dev/lirc0 is the device of your IR receiver)

When you press a button, you will see the raw IR signal received. As I have understand it one of the numbers shown when you press a button should match the number beside the button in the /etc/lirc/lircd.conf file. If they don't you can try to change the /etc/lirc/lircd.conf file.

---

### Post by Trollslayer on 2008-05-04
> **JeepFreak said:**
> Thank you very much for the reply.

As far as the pad goes... I really want it to act in place of the arrow keys (on the keyboard), not control the mouse pointer.  Should I still go the route of the patch?

The link with the keyboard shortcuts is very helpful... Thank you.  I will work on adding more configurations.  I thought, at first, that I had button configured in my ~/.mythtv/lircrc file that were _not_ working in Myth... well, I *do*... but they are the keys that are also not working in irw.

Anybody know why certain buttons are not working in irw?  

Thanks!!
Billy

I've had a look and it seems the reason you need the patch is that the pad replicates mouse actions - e.g. the code returned varies to show how long the pad has been held down since the last code but lirc needs a single code.
Needless to say, I am working on getting the pad sorted myself.

---

### Post by slyhne on 2008-05-05
Hi

Take a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/153184)

I'm going to try the patch this evening, hopefully it solves the problem with the pad.


Regards
slyhne

---

### Post by slyhne on 2008-05-07
Hi

This is what you have to do in order to get the pad working in Hardy:

Install lirc sources and dkms

```
sudo apt-get install dkms lirc-modules-source
```

Copy the patch file (lirc-0.8.3~pre1-0ubuntu7-pad2keys.patch) to /usr/src

```
cp (path)/lirc-0.8.3~pre1-0ubuntu7-pad2keys.patch /usr/src/.
```

Patch the source

```
cd /usr/src/lirc-0.8.3~pre1
sudo patch -p1 < ../lirc-0.8.3~pre1-0ubuntu7-pad2keys.patch
```

Build and install lirc using dkms

```
sudo dkms remove -m lirc -v 0.8.3~pre1 --all
sudo dkms add -m lirc -v 0.8.3~pre1
sudo dkms build -m lirc -v 0.8.3~pre1
sudo dkms install -m lirc -v 0.8.3~pre1
```

Aktiver patch

```
sudo pico /etc/modprobe.d/options
```

Add the following line to the end of this file

> options lirc_imon pad2keys_active=1

Then a reboot, and you ready to navigate MythTV usin the pad.

Have fun

slyhne

---

### Post by Trollslayer on 2008-05-28
I tried this with 8.04 LTS and when it comes to 'dkms add' I get the message "Directoy: /usr/src/lirc-0.8.3~prel doess not exist."
Any suggestions?
At the moment I can get intermittent pad use by selecting one of the codes it uses for each direction but this isn't very reliable.

---

### Post by samarium on 2008-06-01
> **Trollslayer said:**
> I tried this with 8.04 LTS and when it comes to 'dkms add' I get the message "Directoy: /usr/src/lirc-0.8.3~prel doess not exist."
Any suggestions?
At the moment I can get intermittent pad use by selecting one of the codes it uses for each direction but this isn't very reliable.

If /usr/src/lirc-0.8.3~pre1 doesn't exist, then you don't have package lirc-modules-source installed correctly for hardy.

I just followed the process as detailed above and it worked fine for me.  Now I just have to add the mouse key codes the the lircd.conf, and construct a lircrc for mythtv that does what I want.

---

### Post by Trollslayer on 2008-06-01
It exists, I can update using 'make' then 'make install' but the dkms doesn't work.
Ah well, got it working.

---

### Post by lestat289 on 2008-11-07
Hello, I've followed  slyhne's instructions to get iMon Pad working, but the /dev/lirc, /dev/lirc0 and /dev/lcd0 haven't been created... Any idea of what I must do?

PS: Sorry for my poor english, here are 4:00am and my brain is not at best :P

---

### Post by Freddan101 on 2008-11-08
> **lestat289 said:**
> Hello, I've followed  slyhne's instructions to get iMon Pad working, but the /dev/lirc, /dev/lirc0 and /dev/lcd0 haven't been created... Any idea of what I must do?

PS: Sorry for my poor english, here are 4:00am and my brain is not at best :P
I had exactly the same problem in 7.10 and now in 8.10 using Soundgraph Imon Pad. No lirc, lirc0 or lcd0 - just lircd shows up as it did in 7.10. I think I've tried every trick in the book but same poor result remains. Hoped for it to magically work in the new version of Mythbuntu. :( When running dmesg it looks like lirc loads fine though...

---

### Post by IndieRockSteve on 2008-11-09
n/m, the buttons on the remote are just really finicky...

---

