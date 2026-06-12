---
title: "HOWTO: Use the miniature remote that came with your Hauppauge Nova-TD"
date: 2011-10-23
forum: Multimedia Software
---

### Post by s13_mills on 2011-10-23
I recently purchased a Hauppauge Nova-TD to use with my laptop (Asus UL30VT) while I decide which miniature HTPC to buy. I picked the Nova TD because it was the only dual tuner USB stick I could find locally, and I have used Hauppauge Nova-S cards before with good success.

This USB stick is natively supported in Oneiric, I didn't have to do anything fancy to get it recognised/tuning etc. There was one module parameter that I had to change to get it to lock on some of the UK channels, however, just:

```
sudo gedit /etc/modprobe.d/options
```

Then enter:

```
options dvb-usb-dib0700 force_lna_activation=1
```

And save. After that I could see all the channels my TV normally sees without problem in MythTV.

The hardest part of getting this card working fully was the remote (surprise, surprise). I did manage to get it fully functional, although my solution may not be the most eloquent out there. The remote I have is the terrible travel-sized one, part R-005. It's awful to use, and I will probably go and replace it with a Harmony remote once I am done writing this!

To make this awful remote work, I used ir-keytable and LIRC, because I find MythTV and mplayer play nicely with LIRC, and are very configurable. Normally I would have skipped ir-keytable, but in this case it was very useful, since none of the available lircd.conf files had the button maps my remote seemed to have.

Most of the pointers I used for ir-keytable come from [here]("http://forum.xbmc.org/showthread.php?t=101151") - definitely worth a read.

NB: If you already installed LIRC, stop it at this point with:

```
sudo /etc/init.d/lirc stop
```

To start, I copied a readymade configuration from udev into /etc/rc_keymaps to work in:

```
sudo cp /lib/udev/rc_keymaps/hauppauge /etc/rc_keymaps/hauppauge_novaTD
sudo gedit /etc/rc_keymaps/hauppauge_novaTD
```

In a new terminal tab, I ran ir-keytable to find the code for each key on my tiny remote:

```
sudo ir-keytable -t
```

Note that I found the Nova-TD was sending the scancode repeatedly after a single button press - don't worry, I found a workaround for this later.

Edit /etc/rc_keymaps/hauppauge_novaTD with the scancodes you find, and delete any redundant entries. I ended up with:

```
# table hauppauge_novaTD, type: RC5
0x1c25 KEY_SELECT
0x1c3d KEY_POWER
0x1c3b KEY_HOME
0x1c1c KEY_TV
0x1c14 KEY_UP
0x1c15 KEY_DOWN
0x1c16 KEY_LEFT
0x1c17 KEY_RIGHT
0x1c25 KEY_OK
0x1c1f KEY_EXIT
0x1c0d KEY_MENU
0x1c10 KEY_VOLUMEUP
0x1c11 KEY_VOLUMEDOWN
0x1c12 KEY_PREVIOUS
0x1c0f KEY_MUTE
0x1c20 KEY_CHANNELUP
0x1c21 KEY_CHANNELDOWN
0x1c37 KEY_RECORD
0x1c36 KEY_STOP
0x1c32 KEY_REWIND
0x1c35 KEY_PLAY
0x1c34 KEY_FASTFORWARD
0x1c24 KEY_PREVIOUSSONG
0x1c30 KEY_PAUSE
0x1c1e KEY_NEXTSONG
0x1c01 KEY_1
0x1c02 KEY_2
0x1c03 KEY_3
0x1c04 KEY_4
0x1c05 KEY_5
0x1c06 KEY_6
0x1c07 KEY_7
0x1c08 KEY_8
0x1c09 KEY_9
0x1c0a KEY_TEXT
0x1c00 KEY_0
0x1c0e KEY_SUBTITLE
```

Use a different header line and a different name if you called it something different. Save this and close gedit. Once you are done, we will load this keytable by doing the following:

```
sudo ir-keytable -c
sudo ir-keytable -w /etc/rc_keymaps/hauppauge_novaTD
```

The first part is to clear the current table, the second is to write the codes from the file you have created to ir-keytable.

Next is the work-around to deal with the multiple events. This is not pretty and a lot of people may not like it, but it works for me:

```
sudo ir-keytable --period=1410065407
sudo ir-keytable --delay=1410065407
```

Those are the repeat period and repeat delay. Those are the maximum values ir-keytable seems to hold. If you put in a bigger number it just goes to that. The delay and repeat just need to be enough that you are very likely to press another button before the time is up (in this case, within ~16 days!!!!).

To make sure your ir-keytable is rebuilt properly after a reboot, add those lines to rc.local, as below:

```
ir-keytable -c
ir-keytable -w /etc/rc_keymaps/hauppauge_novaTD
ir-keytable --period=1410065407
ir-keytable --delay=1410065407
```

Now we can configure LIRC, I did this by running dpkg-reconfigure lirc, selecting the Nova-T 500 receiver (doesn't really matter though), no sender, and the event-ir input I got from 

```
cat /proc/bus/input/devices
```

If you already did this, then you just need to adjust your /etc/lirc/lircd.conf to suit your situation.

It took a bit of playing to get all the header parameters right in the lircd.conf file, but I ended up with these, which should work for you too.

/etc/lirc/lircd.conf

```
#Configuration for the Hauppauge Nova-T 500 remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge_novaTD_usb"
```

/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge_novaTD_usb

```
#
# brand:                       Hauppauge NOVA-TD
# model no. of remote control: Hauppage Nova-TD R-005
#

begin remote

 name  NOVA-TD_USB
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data        0x8001
 gap          	 100000
 toggle_bit      0

     begin codes
         Go                       0x0162
	 Home			  0x0066
	 Teletext		  0x0184
	 Captions		  0x0172
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x00AE
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x00A5
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x00A3
         1                        0x0002
         2                        0x0003
         3                        0x0004
         4                        0x0005
         5                        0x0006
         6                        0x0007
         7                        0x0008
         8                        0x0009
         9                        0x000A
         *                        0x0037
         0                        0x000B
         #                        0x0029
         one                      0x004F
         two                      0x0050
         three                    0x0051
         four                     0x004B
         five                     0x004C
         six                      0x004D
         seven                    0x0047
         eight                    0x0048
         nine                     0x0049
         ten                      0x0052
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote
```

Now restart LIRC:

```
sudo /etc/init.d/lirc restart
```

After this, I ran irw to check everything was working, you should see something like:

```
andrew@andrew-UL30VT:~$ irw
0000000080010067 00 ArrowUp NOVA-TD_USB
0000000080010069 00 ArrowLeft NOVA-TD_USB
000000008001006a 00 ArrowRight NOVA-TD_USB
000000008001006c 00 ArrowDown NOVA-TD_USB

```

For keypresses of up, left, right, down. Try out all your buttons and make sure they are working as you expect.

Next up, I just used mythbuntu-lirc-generator to make lircrc for all the media apps I normally use (MythTV, mPlayer, VLC etc).

```
sudo apt-get install mythbuntu-lirc-generator
mythbuntu-lirc-generator
```

And that should be it! You should have a fully functioning remote at the end of it! If I have missed a crucial step in the guide, or you have a question, feel free to ask! I hope this saves someone some pain because of a remote!!!

If I do get a Harmony remote, I'll update the guide with how to make that work with the Nova-TD receiver.

---

### Post by s13_mills on 2011-10-26
So I did end up buying a Harmony One, and what a great piece of kit. Definitely recommend it. Dead easy to get it working with my setup too.

After running the Logitech software on my work PC (Windows 7), and designating the Nova-TD as Computer>Media Center PC>Hauppauge>WinTV-Nova-TD (It's obvious when you are going through the wizard), all I had to do was open a terminal and:

```
sudo ir-keytable -c
sudo ir-keytable -w /lib/udev/rc_keymaps/hauppauge
sudo dpkg-reconfigure lirc
```

Where I selected Nova-T500, None and the same event as above. Note that this was necessary because I had the custom lircd.conf from the process above. Once this was done, I edited rc.local:

```
sudo gedit /etc/rc.local
```

Changing it to:

```
ir-keytable -c
ir-keytable -w /lib/udev/rc_keymaps/hauppauge
ir-keytable --period=1410065407
ir-keytable --delay=1410065407
```

I then re-ran mythbuntu-lirc-generator:

```
mythbuntu-lirc-generator
```

And that was all - it worked like a charm, almost too easy ;)!

---

