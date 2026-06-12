---
title: "How to control tvtime volume in ubuntu 11.04 Natty"
date: 2011-07-30
forum: Multimedia Software
---

### Post by dixonstalbert on 2011-07-30
hello

Tvtime built in volume control stopped working in maverick because it depends on kernel support of Open Sound System (oss) and ubuntu kernels are no longer compiled with this turned on.

You can get an experimental deb of tvtime for maverick here:
[https://launchpad.net/~diwic/+archive/maverick]("https://launchpad.net/~diwic/+archive/maverick")

which will work with ALSA sound system.

Here is a partial solution I found on the Russian Ubuntu board by Alexandris if you cannot get the above deb to work for you:

tvtime configuration file at /etc/tvtime/tvtime.xml will allow you to reassign the left and right arrow keys to control whole system volume level while tvtime is running.

Make the following changes in tvtime.xml:

1. comment out existing left and right keybindings by enclosingg them with '<!--', '-->' tags:


```
[COLOR="Red"]<!--[/COLOR]
  <bind command="left">
    <keyboard key="left"/>
    <keyboard key="-"/>
  </bind>

  <bind command="right">
    <keyboard key="right"/>
    <keyboard key="+"/>
  </bind>
[COLOR="red"]-->[/COLOR]
```

2. add the following lines just above or below them:

```
<bind command="run_command" argument="amixer -c 0 sset Line 10-"> 
<keyboard key="left"/> 
</bind>
<bind command="run_command" argument="amixer -c 0 sset Line 10+"> 
<keyboard key="right"/> 
</bind>
```

3. save changes to tvtime.xml and start tvtime in a terminal window and see if there is any error messages. The Russian Ubuntu board recommended using "amixer -c [COLOR="Red"]default[/COLOR]" , but I had to change mine to "amixer -c [COLOR="red"]0[/COLOR]" (the number of my sound card) to get things to work. You might have to do the same...

Good luck.

---

### Post by vigmax on 2011-09-06
much simpler change

1. open terminal and execute "gksudo gedit /etc/tvtime/tvtime.xml"
2. scroll down until you see    <option name="MixerDevice" value="default/mic"/>
3. change the option to    <option name="MixerDevice" value="hw:0/Mic"/>

replace hw:0 to your sound device found by cat /proc/asound/cards and Mic to your and connected channel


that should make tvtime volume control work as normal :o

---

### Post by Rod J on 2011-10-08
> **vigmax said:**
> much simpler change

1. open terminal and execute "gksudo gedit /etc/tvtime/tvtime.xml"
2. scroll down until you see    <option name="MixerDevice" value="default/mic"/>
3. change the option to    <option name="MixerDevice" value="hw:0/Mic"/>

replace hw:0 to your sound device found by cat /proc/asound/cards and Mic to your and connected channel


that should make tvtime volume control work as normal :o

Thanks vigmax, that finally got my tvtime sound working in Kubuntu 11.04! :D

I changed
```
<option name="MixerDevice" value="default/Line"/>
```to

```
<option name="MixerDevice" value="hw:0/Line"/>
```and it worked!

BTW, I couldn't make sense of the output of
```
cat /proc/asound/cards
```which gave me this:

```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 45
```but just using "hw:0/Line" worked just fine.

---

### Post by vigmax on 2011-10-17
> **Rod J said:**
> Thanks vigmax, that finally got my tvtime sound working in Kubuntu 11.04! :grin:
BTW, I couldn't make sense of the output of
```
cat /proc/asound/cards
```which gave me this:

```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 45
```

multiple sound cards need the correct index number from cat /proc/asound/cards
if u have multiple sound cards it will be listed by the command
```
_**0**_ [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 45
```:D:D

---

### Post by ene_dene on 2011-11-05
Thanks a bunch!
I've just installed Kubuntu 11.10 and couldn't see what I was doing wrong, this solved the problem with my analog TVcard and tvtime.

---

### Post by Tosa on 2011-11-06
Thanks guys, tvtime finally talks to me again!

I've changed the line

<option name="MixerDevice" value="/dev/mixer:mic>

to

<option name="MixerDevice" value="default/Line"/>

and it works...

---

