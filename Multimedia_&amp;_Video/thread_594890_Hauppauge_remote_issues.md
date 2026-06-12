---
title: "Hauppauge remote issues"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by scweston on 2007-10-28
Hi,

I'm trying to use the Hauppauge remote control to work in mythtv. I have the hauppauage nova t 500 card, which after a lot of effort and fiddling I managed to get working with mythtv, but the remote control that came with it still eludes me.

The arrow keys appear to get me around the menus and the volume buttons change the volume, but there is no response from any of the other keys.

I have followed the wiki guide here
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
However I don't appear to get the expected output from the irw command. Here is an example of my output after pressing the remote control's arrow keys  followed by the number keys below: -

> stephen@stephen-desktop:~$ irw
^[[A^[[D^[[C^[[B123456789

The vast majority of the keys on the remote produce no response in irw. But as you can see this output looks very different to the example given in the guide.

Please, any help would be appreciated. I'm very close to being a very happy ubuntu and mythtv user, just not quite there yet!

Stephen

---

### Post by bconverse on 2007-10-30
I hope someone can help with this one, I am having the same problem, only with the Hauppauge WinTv PVR 350 Remote (the black and grey 45 button one). I can also navigate around the menus fine with the arrows, but, most of the other functions of the remote don't work.

---

### Post by scweston on 2007-11-03
Hi,

Hi, after a week I'm still struggling with the same issues I mentioned in post 1. In an effort to get try to get more help I wish to give some extra information that I think may be relevant.

First if all here is the contents of /etc/lirc/hardware.conf :-

> # /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/input/event4"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

And here is how my remote control appears in $cat /proc/bus/input/devices

> I: Bus=0003 Vendor=2040 Product=9950 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:02.2-1/ir0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10afc332 2842845 0 0 0 4 80018000 2180 40000801 9e96c0 0 800200 ffc


Also, incase it helps anyone to help me, here is the contents of the /etc/lirc/lircd.conf :-

```
#
# brand:                       Hauppauge NOVA-T-500
# model no. of remote control: Hauppage Nova-T-500 Snowboard Shape Silver over Black
#

begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0


     begin codes
         Go                       0x0162
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
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197
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
         Red                      0x018E
         Green                    0x018F
         Yellow                   0x0190
         Blue                     0x0191
     end codes

end remote
```



Again, I would really appreciate anybody's suggestions on what I could try to get my remote fully working.

Stephen

My equipment:
Hauppage WinTV Nova T 500
Ubuntu Gutsy 32bit
AMD Athlon 64 x2 4200+
2GB memory
Foxconn NF2SK8AA motherboard
nVidia Geforce 7600GS graphics

---

### Post by sygin on 2008-01-05
Hi,

I have got everything working, my only problem is that I have to power
down my box every few days (some issue with usb disconnect bug I think).

I followed this guide:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Pay special attention to:
"This is a sample /home/mythtv/.lircrc"

The above file must be present in your users home directory 
e.g.   /home/bob/.lircrc

You must also link this file to /home/bob/.mythtv/lircrc
e.g.       ln -s /home/bob/.lircrc /home/bob/.mythtv/lircrc

Where "bob" represents the username that is used to launch the mythfrontend.


To get the modules to compile I had to install the linux-headers-2.6.22-13-386
package, the exact version depends on the kernel you are using.

To find my Linux Kernel version. I used:
uname -r

I also had to use the command:
sudo ln -s /usr/src/linux-headers-2.6.22-13-386 /lib/modules/2.6.22-13-386/source

to get the v4l modles to compile, replace 2.6.22-13-386 with your kernel version.

This was the only way I got the remote to work.

Another tip, the firmware only loads when you power cycle your box. So do that
before giving up.

Cheers
Sygin

PS: I am using gutsy beta but feisty will work.

---

### Post by stevanbt on 2008-02-24
Hi,
I had the same issues with my Nova 500 remote control, irw displayed
```
^[[A^[[D^[[C^[[B123456789
```

I think it was due to the /etc/lirc/hardware.conf referencing the wrong device.  I'm not sure I totally understand what's happening, but I found the section on "Make the LIRC Device Static" useful [http://parker1.co.uk/mythtv_tips.php]("http://parker1.co.uk/mythtv_tips.php")

Hope this helps someone.

Thanks, Steve.

---

