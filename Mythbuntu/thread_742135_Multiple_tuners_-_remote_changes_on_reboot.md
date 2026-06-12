---
title: "Multiple tuners - remote changes on reboot"
date: 2008-04-01
forum: Mythbuntu
---

### Post by RichardA on 2008-04-01
I have two Nova T-500 tuners. The receiver for the remote is plugged into one of them. When I reboot, the tuners can be picked up in a different order and I have to edit a lirc config file and restart lirc to get the remote to work again.

Is it possible to write a udev rule which can distinguish between the two identical tuner cards, so I can point to an unchanging location for the remote receiver? Something to do with the PCI id, perhaps?

---

### Post by oscarsfriend on 2008-04-01
Sure -- identify by pci slot, as you say.  I have two nova-t dvb pci cards (not 500), and had the same problem.  See this link: [http://ubuntuforums.org/showthread.php?t=589545](http://ubuntuforums.org/showthread.php?t=589545)

---

### Post by KillerKiwi on 2008-04-01
Heres a script that will create a udev rule for you

usage

sudo python udev-rules.py /dev/existing_device /dev/new_device_point

---

### Post by RichardA on 2008-04-02
Maybe I'm being a bit slow here. Am I calling the script with the wrong parameters?:
```

tv@sest:~$ python udev-rules.py /dev/event2 /dev/irdevice
Traceback (most recent call last):
  File "udev-rules.py", line 33, in <module>
    kernel = re.search("KERNEL\=\=\".+\"", attributes).group()
AttributeError: 'NoneType' object has no attribute 'group'

```

I'd write the rule manually, but I can't see what's different for the two IR receivers:
```

tv@sest:~$ dmesg | grep IR-rec
[   37.090425] input: IR-receiver inside an USB DVB receiver as /class/input/input2
[   38.249186] input: IR-receiver inside an USB DVB receiver as /class/input/input3

tv@sest:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event2) | grep modalias
ATTRS{modalias}=="input:b0003v2040p9950e0100-e0,1,k71,72,73,74,77,80,8B,9E,A4,A7,A8,AD,CF,D0,D2,DF,E2,160,162,163,166,16B,16D,172,177,179,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19A,19C,ramlsfw"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001106sd00003104bc0Csc03i20"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
 
tv@sest:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event3) | grep modalias
    ATTRS{modalias}=="input:b0003v2040p9950e0100-e0,1,k71,72,73,74,77,80,8B,9E,A4,A7,A8,AD,CF,D0,D2,DF,E2,160,162,163,166,16B,16D,172,177,179,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19A,19C,ramlsfw"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001106sd00003104bc0Csc03i20"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"

```

---

### Post by oscarsfriend on 2008-04-02
Look for the KERNELS line in the output of the udevinfo (i.e. don't grep for modalias).

This is what I get:
```

$ dmesg | grep "cx88 IR"

[   30.202666] input: cx88 IR (Hauppauge Nova-T DVB-T as /class/input/input3
[   30.350597] input: cx88 IR (Hauppauge Nova-T DVB-T as /class/input/input5

$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event3) | grep KERNELS
    KERNELS=="input3"
    [COLOR="Red"]KERNELS=="0000:01:09.0"[/COLOR]
    KERNELS=="0000:00:08.0"
    KERNELS=="pci0000:00"

$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event5) | grep KERNELS
    KERNELS=="input5"
    [COLOR="Red"]KERNELS=="0000:01:0a.0"[/COLOR]
    KERNELS=="0000:00:08.0"
    KERNELS=="pci0000:00"

```

My udev rule is:
```

KERNEL=="event*",SYSFS{vendor}=="0x14f1",[COLOR="Red"]KERNELS== "0000:01:09.*"[/COLOR],SYMLINK="input/irremote"

```
Note the * in the KERNELS bit (the number after the "1:09." can change on rebooting, for my set-up).

And just for the sake of clarity:
```

$ ls -l /dev/input/irremote
lrwxrwxrwx 1 root root 6 2008-04-02 17:56 /dev/input/irremote -> event3

```

---

### Post by KillerKiwi on 2008-04-02
> **RichardA said:**
> Maybe I'm being a bit slow here. Am I calling the script with the wrong parameters?:
```

tv@sest:~$ python udev-rules.py /dev/event2 /dev/irdevice
Traceback (most recent call last):
  File "udev-rules.py", line 33, in <module>
    kernel = re.search("KERNEL\=\=\".+\"", attributes).group()
AttributeError: 'NoneType' object has no attribute 'group'

```

I'd write the rule manually, but I can't see what's different for the two IR receivers:
```

tv@sest:~$ dmesg | grep IR-rec
[   37.090425] input: IR-receiver inside an USB DVB receiver as /class/input/input2
[   38.249186] input: IR-receiver inside an USB DVB receiver as /class/input/input3

tv@sest:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event2) | grep modalias
ATTRS{modalias}=="input:b0003v2040p9950e0100-e0,1,k71,72,73,74,77,80,8B,9E,A4,A7,A8,AD,CF,D0,D2,DF,E2,160,162,163,166,16B,16D,172,177,179,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19A,19C,ramlsfw"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001106sd00003104bc0Csc03i20"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
 
tv@sest:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/event3) | grep modalias
    ATTRS{modalias}=="input:b0003v2040p9950e0100-e0,1,k71,72,73,74,77,80,8B,9E,A4,A7,A8,AD,CF,D0,D2,DF,E2,160,162,163,166,16B,16D,172,177,179,181,182,184,185,188,189,18E,18F,190,191,192,193,195,197,19A,19C,ramlsfw"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001106sd00003104bc0Csc03i20"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"

```


try using  /dev/input/event2 as the input not /dev/event2

I've added a bit of magic/checking to the script this issue seems to come up for a lot of people.... I might look at a small ui next...

Let me know if that works

---

### Post by RichardA on 2008-04-04
Done!
```

KERNEL=="event*",SYSFS{vendor}=="0x1106",KERNELS=="0000:04:01.2",SYMLINK="input/irremote"

```
I was trying to use idVendor instead of vendor, because it was closer in the udev tree to the device, but once I used vendor it worked. Thanks.

Killerkiwi: Thanks for the script. I edited the config by hand because it's easier to put in my build notes than a script (the one certain thing is that I will break and rebuild my Myth box). It would be good to see a link to your script in the Mythbuntu Control Centre, though, with an explanation on how to work out the parameters to it.

---

### Post by oscarsfriend on 2008-04-04
> **RichardA said:**
> 
```

KERNEL=="event*",SYSFS{vendor}=="0x1106",KERNELS=="0000:04:01.[COLOR="Red"]**2**[/COLOR]",SYMLINK="input/irremote"

```


You might want to check that the number I highlighted above doesn't change on reboot for your IR device.  For me it does, which is why I used a * wildcard there.

---

### Post by RichardA on 2008-04-04
I saw you had a wildcard but mine didn't change over a couple of reboots, so I left it as-is. If it stops working, that's the first thing I'll check.

---

