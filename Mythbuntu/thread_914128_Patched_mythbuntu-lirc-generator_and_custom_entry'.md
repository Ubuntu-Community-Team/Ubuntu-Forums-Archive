---
title: "Patched mythbuntu-lirc-generator and custom entry's for WinTV-HVR-1110"
date: 2008-09-08
forum: Mythbuntu
---

### Post by db260179 on 2008-09-08
Hello,

Please find a patched mythbuntu-lirc-generator_0.20-1ubuntu1_all.deb - I've changed the ok and enter settings, so duplicates dont occur.

And a added entry for HVR-1110 as 1100 doesnt work correctly in the lirc.hwdb. I added a lircd.conf.hauppaugehvr-1110 for HVR-1110 for better compatibility.

Hope this helps Wintv-HVR-1110 owners?

Please install the version from intrepid - lirc.0.8.3


Howto install:

Copy the lirc.hwdb to /usr/share/lirc and copy the lircd.conf.hauppaugehvr-1110 to /usr/share/lirc/remotes/hauppauge

Install the deb as normal.In the control-centre you should see an entry for HVR-1110.

---

### Post by Finswimmer on 2008-11-07
Hello,
I downloaded and installed your files.
My Remote is recocnized as /dev/input/event7.
It is working but the Back Button is not working.

lircd -H devinput -d /dev/input/event7 -n is the way I start my lircd.
But irw does not show anything.

What can I do to improve/verify it?

Thanks
Tobi

---

### Post by tgm4883 on 2008-11-08
If you would like to get this into Mythbuntu, please file a bug report at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu) and attach your patch

---

### Post by Serge-Enrico on 2008-12-13
Thanks for your patch db260179. 

Unfortunately I cannot get the Back/Exit button get to work, just like Finswimmer. I have been searching forums and howto's but couldn't find the answer. After endless changing the hardware.conf lirc.conf and other files I still cannot get the back button to work. I am using Mythbuntu8.10. I hope you can be of any help. Please let me know which output I can provide to make it more clear. BTW, I am a complete noob in linux/mythbuntu :confused:

Thanks, Enrico

---

### Post by antebe on 2008-12-25
I am having the same problem with Back/Exit button, and actually most buttons. The only buttons that work for me after installing the patch (and before, nothing changed with the patch) are the Power button, the OK and 4 direction arrows around it, the volume+/- and mute buttons, and the numerical buttons.

I tried a workaround, and modified the "0" button to "config = Escape" but that does not change the behavior of this button. How come? In the frontend log it says that lirc successfully initiated using the very same file. I have tried restarting lirc, rebooting the computer, but nothing helps.

I found another thing I find strange, but I am a Linux newbie and still don't understand the details: If I remove the lirc package, the remote is still working, with the same buttons as I mentioned above, and no others. Isn't that strange? 

If I stop lirc and then run
 
sudo lircd -H dev/input -d /dev/input/event6 -n in one window

and 

irw 

in another terminal window, I get output only from the buttons mentioned above.

---

### Post by antebe on 2008-12-27
Thanks to some wonderful help I got from laga today, who pointed me to a bug thread [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/204960) I got a step further. But the remote still does not work inside mythtv and other applications.

Here is what I did:
I followed the bug workaround and installed inputlirc:
sudo aptitude install inputlirc

Then I issued a
cat /proc/bus/input/devices

to find out my IR device was event7, so I modified /etc/default/inputlirc to be
EVENTS="/dev/input/event7"
OPTIONS="-g -m 0"

In order to find what to put into the remote.fdi file that is mentioned in the bug thread, I did an output of hal and found out that this should be my /usr/share/hal/fdi/preprobe/20thirdparty/remote.fdi file content:

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
<device>
 <match key="info.product" contains_ncase="HVR 1110">
  <merge key="info.ignore" type="bool">true</merge>
 </match>
</device>
</deviceinfo>

After this I restarted lirc and inputlirc:
sudo /etc/init.d/lirc restart
sudo /etc/init.d/inputlirc start

After this the remote is no longer acting as a keyboard, and irw gives correct outputs, for example:
1c 0 KEY_ENTER event7

...if I press the OK button.

BUT: Now comes the problem: The remote now does not work at all inside any application, mythtv or mplayer. It is completely dead. 

ircat mythtv

...gives no output, just hangs.

I have tried just about every possible setting in my hardware.conf file, and I have made sure that the .lirc/mythtv file corresponds with my /etc/lircd.conf file.

irrecord does not work in this case. if I try 

sudo irrecord -d /dev/input/event7 -H devinput test.conf

I get the output after pressing RETURN and then holding a button down on the remote:
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event7'

If I kill the lirc process, and then run
sudo lircd -d /dev/input/event7

then suddenly irw does NOT work, but strangely
sudo irrecord -d /dev/input/event7 -H devinput test.conf

...does. And the funny thing is, that now SOME buttons work inside mythtv and mplayer, but only a few, and nothing is correlated to changes I make in the .lirc/mythtv files...

I am not sure this is a hint to what goes wrong here...?

My /etc/lirc/hardware.conf includes:
REMOTE="Hauppauge HVR-1110"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

I would appreciate if someone might have an idea on what to do...

---

### Post by antebe on 2008-12-27
OK, I found a solution at last. I erroneously assumed that the "KEY_" in the output from irw was not going to be part of the actual name in the .lircrc inputs. But adding the entries in my .lircrc with, for example
button = KEY_LEFT
config = Left

made it all work!

The only thing now is to figure out where lirc and irw gets these names from, it is for sure not in my /etc/lircd.conf file.

I hope my posts can help some of you other guys with the same problem. I spent an unreasonable amount of time on this...

---

### Post by Serge-Enrico on 2008-12-28
Hi antebe,

Thanks for giving updates on this problem. It is a pity that the Hauppauge 1110 is not supported out-of-the-box. After installing mythbuntu 8.10 I used the above-mentioned patch from db260179. Unfortunately the remote still didn't work. After following this thread:

[http://ubuntuforums.org/showthread.php?t=933126]("http://ubuntuforums.org/showthread.php?t=933126")

I could finally watch some TV channels and the remote was kind of working (only the arrow,OK and number buttons).

It appears that the remote-control support for the Hauppauge 1110 is build into the kernel via the V4L-DVB module. That's the reason why the remote works without LIRC. However, on the V4L website there is an explanation how to get it working with lircd.

[http://www.linuxtv.org/wiki/index.php/Remote_controllers-V4L]("http://www.linuxtv.org/wiki/index.php/Remote_controllers-V4L")

When running irrecord I also get the "gap not found, can't continue" error, even after "just clicking the buttons" as explained in the wiki. Somehow the remote control is seen as a keyboard by the kernel and we should be able to configure the buttons via lirc. The problem is I know too few about linux to get this working.

Maybe somebody is out there who can help us?

---

### Post by antebe on 2008-12-29
Serge,

Just to clarify: My remote now works exactly as you want it to (although I do not understand why). That means all buttons work. Just follow the points I hinted at. 

The key points are: to add inputlirc, a remote.fdi file as suggested, and in my case I had to use the names KEY_XXXX in the .lircrc file.

---

### Post by Serge-Enrico on 2009-01-02
Hi antebe,

Thanks for your help. It took some time to figure it all out but my remote is still not working. What I did thus far:

1.Installed mythbuntu
2.Installed db260179's patch
3.Installed V4L-DVB as mentioned earlier (I need this to get the Hauppauge HVR-1110 working at all)

At this stage I can watch TV channels, I have sound and a partly working remote (irw and irrecord do not work as most of the buttons)

4.cat /proc/bus/input/devices shows that my remote is event5
5.Installed inputlirc and edited the options to event5
6.Installed remote.fdi

At this moment irw does give me the KEY_XXX output but the remote does not work at all in mythtv as you encountered as well. I changed the .lirc/mythtv file so it says:

Begin
   remote = hvr1110
   prog = mythtv
   button = KEY_LEFT
   config = Left
end

etc.etc.

I entered all "button = KEY_XXXX" as stated by IRW. My remote is still doing nothing. Then I put the keys directly into the .lircrc file and deleted the "include ~/.lirc/mythtv" line but this also didn't work. My /etc/lirc/hardware.conf file is the same as yours.

It seems that you have done something in the last part that I haven't but I can't figure it out. Do you remember if you changed any other files? The weird thing is that when I run "lshal | grep lirc" it doesn't return anything.

Like you I have spend un unreasonable amount of time on this subject, fortunately you were more succesfull. I hope you still have the energy to give me a bit of help :-)

---

### Post by antebe on 2009-01-02
Have you checked your log files after you enter and exit mythtv? You should see a line in the frontend log saying something like "lirc init successful using file /home/username/.mythtv/lircrc", or perhaps there is a clue to what goes wrong.

If you have irw getting you correct output I think you are close! :D

---

### Post by mirak63 on 2009-02-15
hi,

I have a similar issue with a TechnoTrend C1500 which is a DVB Cable card. TechnoTrend and hauppauge are similar they use the same hardware.
What is interesting is that this card is really not new, it's second hand and I have it since 3 years, so it's maybe 5 years old.

The remote is bound to event5 

cat /proc/bus/input/devices
```
I: Bus=0001 Vendor=13c2 Product=1010 Version=0001
N: Name="Budget-CI dvb ir receiver saa7146 (1)"
P: Phys=pci-0000:05:07.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:09.0/0000:05:07.0/input/input9
U: Uniq=
H: Handlers=kbd event5 
B: EV=100003
B: KEY=40fc010 20206100000000 0 8000 418080002001 9e168000000000 ffc
```

what I don't understand is why the ir is associated to kbd
which of course made my telecomand act like keys of a multimedia keyboard

---

