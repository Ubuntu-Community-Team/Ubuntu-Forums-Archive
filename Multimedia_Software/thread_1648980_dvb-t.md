---
title: "dvb-t"
date: 2010-12-19
forum: Multimedia Software
---

### Post by then_dude on 2010-12-19
hello everybody,

i had installed my usb dvb-t dongle, but on a new pc i doesn't work. 

i had tried on the old pc lost of things, and all of a sudden it worked. 
but i don't know why it worked; 

so here we go again. 

i have an ec168 usb dongle mxl5003

the lsusb command shows the dongle

i have done the next things

0/ disconnect the dongle 
1/ sudo apt-get install mercurial linux-firmware-nonfree
2/ hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
3/ cd v4l-dvb
4/  make 
5/ Edite "v4l/.config", CONFIG_DVB_FIREDTV=n
6/ make
7/ if there is an error   ir-sysfs.c  : replace content file  v4l-dvb/linux/drivers/media/IR/ir-sysfs.c 
```
 /* ir-sysfs.c - sysfs interface for RC devices (/sys/class/rc)
 *
 * Copyright (C) 2009-2010 by Mauro Carvalho Chehab <mchehab@redhat.com>
 *
 * This program is free software; you can redistribute it and/or modify
 *  it under the terms of the GNU General Public License as published by
 *  the Free Software Foundation version 2 of the License.
 *
 *  This program is distributed in the hope that it will be useful,
 *  but WITHOUT ANY WARRANTY; without even the implied warranty of
 *  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *  GNU General Public License for more details.
 */

#include <linux/slab.h>
#include <linux/input.h>
#include <linux/device.h>
#include "ir-core-priv.h"

#define IRRCV_NUM_DEVICES    256

/* bit array to represent IR sysfs device number */
static unsigned long ir_core_dev_number;

/* class for /sys/class/rc */
static char *ir_devnode(struct device *dev, mode_t *mode)
{
    return kasprintf(GFP_KERNEL, "rc/%s", dev_name(dev));
}

static struct class ir_input_class = {
    .name        = "rc",
    .devnode    = ir_devnode,
};

/**
 * show_protocol() - shows the current IR protocol
 * @d:        the device descriptor
 * @mattr:    the device attribute struct (unused)
 * @buf:    a pointer to the output buffer
 *
 * This routine is a callback routine for input read the IR protocol type.
 * it is trigged by reading /sys/class/rc/rc?/current_protocol.
 * It returns the protocol name, as understood by the driver.
 */
static ssize_t show_protocol(struct device *d,
                 struct device_attribute *mattr, char *buf)
{
    char *s;
    struct ir_input_dev *ir_dev = dev_get_drvdata(d);
    u64 ir_type = ir_dev->rc_tab.ir_type;

    IR_dprintk(1, "Current protocol is %lld\n", (long long)ir_type);

    /* FIXME: doesn't support multiple protocols at the same time */
    if (ir_type == IR_TYPE_UNKNOWN)
        s = "Unknown";
    else if (ir_type == IR_TYPE_RC5)
        s = "rc-5";
    else if (ir_type == IR_TYPE_NEC)
        s = "nec";
    else if (ir_type == IR_TYPE_RC6)
        s = "rc6";
    else if (ir_type == IR_TYPE_JVC)
        s = "jvc";
    else if (ir_type == IR_TYPE_SONY)
        s = "sony";
    else
        s = "other";

    return sprintf(buf, "%s\n", s);
}

/**
 * store_protocol() - shows the current IR protocol
 * @d:        the device descriptor
 * @mattr:    the device attribute struct (unused)
 * @buf:    a pointer to the input buffer
 * @len:    length of the input buffer
 *
 * This routine is a callback routine for changing the IR protocol type.
 * it is trigged by reading /sys/class/rc/rc?/current_protocol.
 * It changes the IR the protocol name, if the IR type is recognized
 * by the driver.
 * If an unknown protocol name is used, returns -EINVAL.
 */
static ssize_t store_protocol(struct device *d,
                  struct device_attribute *mattr,
                  const char *data,
                  size_t len)
{
    struct ir_input_dev *ir_dev = dev_get_drvdata(d);
    u64 ir_type = 0;
    int rc = -EINVAL;
    unsigned long flags;
    char *buf;

    while ((buf = strsep((char **) &data, " \n")) != NULL) {
        if (!strcasecmp(buf, "rc-5") || !strcasecmp(buf, "rc5"))
            ir_type |= IR_TYPE_RC5;
        if (!strcasecmp(buf, "nec"))
            ir_type |= IR_TYPE_NEC;
        if (!strcasecmp(buf, "jvc"))
            ir_type |= IR_TYPE_JVC;
        if (!strcasecmp(buf, "sony"))
            ir_type |= IR_TYPE_SONY;
    }

    if (!ir_type) {
        IR_dprintk(1, "Unknown protocol\n");
        return -EINVAL;
    }

    if (ir_dev->props && ir_dev->props->change_protocol)
        rc = ir_dev->props->change_protocol(ir_dev->props->priv,
                            ir_type);

    if (rc < 0) {
        IR_dprintk(1, "Error setting protocol to %lld\n",
               (long long)ir_type);
        return -EINVAL;
    }

    spin_lock_irqsave(&ir_dev->rc_tab.lock, flags);
    ir_dev->rc_tab.ir_type = ir_type;
    spin_unlock_irqrestore(&ir_dev->rc_tab.lock, flags);

    IR_dprintk(1, "Current protocol(s) is(are) %lld\n",
           (long long)ir_type);

    return len;
}

static ssize_t show_supported_protocols(struct device *d,
                 struct device_attribute *mattr, char *buf)
{
    char *orgbuf = buf;
    struct ir_input_dev *ir_dev = dev_get_drvdata(d);

    /* FIXME: doesn't support multiple protocols at the same time */
    if (ir_dev->props->allowed_protos == IR_TYPE_UNKNOWN)
        buf += sprintf(buf, "unknown ");
    if (ir_dev->props->allowed_protos & IR_TYPE_RC5)
        buf += sprintf(buf, "rc-5 ");
    if (ir_dev->props->allowed_protos & IR_TYPE_NEC)
        buf += sprintf(buf, "nec ");
    if (buf == orgbuf)
        buf += sprintf(buf, "other ");

    buf += sprintf(buf - 1, "\n");

    return buf - orgbuf;
}

#define ADD_HOTPLUG_VAR(fmt, val...)                    \
    do {                                \
        int err = add_uevent_var(env, fmt, val);        \
        if (err)                        \
            return err;                    \
    } while (0)

static int ir_dev_uevent(struct device *device, struct kobj_uevent_env *env)
{
    struct ir_input_dev *ir_dev = dev_get_drvdata(device);

    if (ir_dev->rc_tab.name)
        ADD_HOTPLUG_VAR("NAME=%s", ir_dev->rc_tab.name);
    if (ir_dev->driver_name)
        ADD_HOTPLUG_VAR("DRV_NAME=%s", ir_dev->driver_name);

    return 0;
}

/*
 * Static device attribute struct with the sysfs attributes for IR's
 */
static DEVICE_ATTR(protocol, S_IRUGO | S_IWUSR,
           show_protocol, store_protocol);

static DEVICE_ATTR(supported_protocols, S_IRUGO | S_IWUSR,
           show_supported_protocols, NULL);

static struct attribute *ir_hw_dev_attrs[] = {
    &dev_attr_protocol.attr,
    &dev_attr_supported_protocols.attr,
    NULL,
};

static struct attribute_group ir_hw_dev_attr_grp = {
    .attrs    = ir_hw_dev_attrs,
};

static const struct attribute_group *ir_hw_dev_attr_groups[] = {
    &ir_hw_dev_attr_grp,
    NULL
};

static struct device_type rc_dev_type = {
    .groups        = ir_hw_dev_attr_groups,
    .uevent        = ir_dev_uevent,
};

static struct device_type ir_raw_dev_type = {
    .uevent        = ir_dev_uevent,
};

/**
 * ir_register_class() - creates the sysfs for /sys/class/rc/rc?
 * @input_dev:    the struct input_dev descriptor of the device
 *
 * This routine is used to register the syfs code for IR class
 */
int ir_register_class(struct input_dev *input_dev)
{
    int rc;
    const char *path;
    struct ir_input_dev *ir_dev = input_get_drvdata(input_dev);
    int devno = find_first_zero_bit(&ir_core_dev_number,
                    IRRCV_NUM_DEVICES);

    if (unlikely(devno < 0))
        return devno;

    if (ir_dev->props) {
        if (ir_dev->props->driver_type == RC_DRIVER_SCANCODE)
            ir_dev->dev.type = &rc_dev_type;
    } else
        ir_dev->dev.type = &ir_raw_dev_type;

    ir_dev->dev.class = &ir_input_class;
    ir_dev->dev.parent = input_dev->dev.parent;
    dev_set_name(&ir_dev->dev, "rc%d", devno);
    dev_set_drvdata(&ir_dev->dev, ir_dev);
    rc = device_register(&ir_dev->dev);
    if (rc)
        return rc;


    input_dev->dev.parent = &ir_dev->dev;
    rc = input_register_device(input_dev);
    if (rc < 0) {
        device_del(&ir_dev->dev);
        return rc;
    }

    __module_get(THIS_MODULE);

    path = kobject_get_path(&ir_dev->dev.kobj, GFP_KERNEL);
    printk(KERN_INFO "%s: %s as %s\n",
        dev_name(&ir_dev->dev),
        input_dev->name ? input_dev->name : "Unspecified device",
        path ? path : "N/A");
    kfree(path);

    ir_dev->devno = devno;
    set_bit(devno, &ir_core_dev_number);

    return 0;
};

/**
 * ir_unregister_class() - removes the sysfs for sysfs for
 *               /sys/class/rc/rc?
 * @input_dev:    the struct input_dev descriptor of the device
 *
 * This routine is used to unregister the syfs code for IR class
 */
void ir_unregister_class(struct input_dev *input_dev)
{
    struct ir_input_dev *ir_dev = input_get_drvdata(input_dev);

    clear_bit(ir_dev->devno, &ir_core_dev_number);
    input_unregister_device(input_dev);
    device_del(&ir_dev->dev);

    module_put(THIS_MODULE);
}

/*
 * Init/exit code for the module. Basically, creates/removes /sys/class/rc
 */

static int __init ir_core_init(void)
{
    int rc = class_register(&ir_input_class);
    if (rc) {
        printk(KERN_ERR "ir_core: unable to register rc class\n");
        return rc;
    }

    /* Initialize/load the decoders/keymap code that will be used */
    ir_raw_init();

    return 0;
}

static void __exit ir_core_exit(void)
{
    class_unregister(&ir_input_class);
}

module_init(ir_core_init);
module_exit(ir_core_exit);
```

8/ sudo make install
9/ ajouter l'utilisateur courant aux groupes "video" et "audio"
10/ connect the dongle
11/ Reboot
12/ Enjoy !


STEP: 9 i haven't done it: it was taken from a french site, i don't know how to add it to video and audio. 

but ubuntu 10.04 shows up and tells me that the 

firmware for dvb drivers is used. 
e3c ec168  dvb-t usb 2.0 driver is used. 

but i cannot select a dvb-t device, or the dongle itself is not getting hot, what is indication of communication with it. 

anybody see the problem ? cannot be that far from functioning it think. 
thanks a lot

greetz

---

### Post by Agent Smith on 2010-12-19
Have you added the ec168.fw in /lib/firmware folder?

---

### Post by Agent Smith on 2010-12-19
I forgot to say to add it to the latest kernel folder in /lib/firmware.

---

### Post by then_dude on 2010-12-19
dvb-usb-ec168.fw is in the lib/firmware

that's oke i suppose ?

---

### Post by markthekdeguy on 2010-12-21
Ubuntu comes with quite  a good few DVB firmwares already.
when i try different distro's out i just drop the firmware file
into /lib/firmware as mentioned above, fire up Kaffeine, goto channels
and scan :)

have you tried Kaffeine ? i love the old qt3 version. solid bit of code :)
google for kaffeine_0.8.7-1ubuntu5.1_i386.deb
or use the newer flakier version out of synaptic, which will keep buggin u theres an update, until u lock version..

good luck

---

### Post by then_dude on 2010-12-28
thanks guys, i have copied to all directories mentioned above, so far no change,

i run kaffeine, but i cannot make it start to scan 
i cannot choose source either

strange 
thanks

---

### Post by size_XXM on 2010-12-28
Run tailf /varl/log/kern.log, (re-)plug the tuner and post the output here. Post the dongle's USB-ID.

---

### Post by then_dude on 2010-12-31
Dec 31 17:14:41 dude-desktop kernel: [ 7019.332122] usb 1-3.4: new high speed USB device using ehci_hcd and address 7
Dec 31 17:14:41 dude-desktop kernel: [ 7019.424773] usb 1-3.4: configuration #1 chosen from 1 choice
Dec 31 17:14:41 dude-desktop kernel: [ 7019.426778] input: HID 18b4:1689 as /devices/pci0000:00/0000:00:02.2/usb1/1-3/1-3.4/1-3.4:1.0/input/input7
Dec 31 17:14:41 dude-desktop kernel: [ 7019.427011] generic-usb 0003:18B4:1689.0004: input,hidraw1: USB HID v1.11 Keyboard [HID 18b4:1689] on usb-0000:00:02.2-3.4/input0

this is what came up when i inserted the dongle

thanks

---

### Post by size_XXM on 2010-12-31
That looks like the driver's never being loaded - as if it wasn't recognized :-\ It looks like the combination of EC168+MXL5003 is supposed to work. Don't know if it's in the mainline yet, according to [the wiki](http://www.linuxtv.org/wiki/index.php/E3C_EC168) you'll need to use the special ec168 repository: [http://linuxtv.org/hg/~anttip/ec168/](http://linuxtv.org/hg/~anttip/ec168/)
Build and install the drivers from there and see if it works. Or check the commits to the mainline to see if it's there already.

EDIT: On second thought, the logs being empty might not be a good indication whether the driver is loaded. How about *lsmod | grep dvb*, or simply *ls /dev/dvb*? If there's no relevant dvb module loaded then something's wrong with the system, the absence of /dev/dvb/adapter* file would indicate the driver is not working.

---

### Post by then_dude on 2011-01-01
thanks a lot size_XXM,

great explanation. i have found no dvb in my /dev folder. so the driver isn't loaded. something which i can also check by the temperature of the dongle. 

i have used the driver you mentioned. 

but i will go over all the steps again and report back.

thanks a lot

---

### Post by then_dude on 2011-01-01
it's working guys

thanks a lot

with the explanation made i could figure out what i was doing instead of just copying the commands. 

it is as simple as downloading the anttip/ec168 file and extracting it. 

then follow the commands of my first post

and make shure the driver is in the right directory, 

and hé it should work. 

thanks a lot again

---

### Post by gunner814 on 2012-04-17
Hello
ther is a problem with the ec-168 repository when I try to clone it using mercurial I get this result

hg clone [http://linuxtv.org/hg/~anttip/ec168/]("http://linuxtv.org/hg/%7Eanttip/ec168/")

abort: 'http://linuxtv.org/hg/~anttip/ec168/' does not appear to be an hg repository:
---%<--- (text/html; charset=UTF-:cool:
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en-US">
<head>
<link rel="icon" href="/hg/static/hgicon.png" type="image/png" />
<meta name="robots" content="index, nofollow" />
<link rel="stylesheet" href="/hg/static/style-paper.css" type="text/css" />

<title>Mercurial repositories index</title>
</head>
<body>

<div class="container">
<div class="menu">
<a href="http://mercurial.selenic.com/">
<img src="/hg/static/hglogo.png" width=75 height=90 border=0 alt="mercurial" /></a>
</div>
<div class="main">
<h2>Mercurial Repositories</h2>

<table class="bigtable">
    <tr>
        <th><a href="?sort=name">Name</a></th>
        <th><a href="?sort=description">Description</a></th>
        <th><a href="?sort=contact">Contact</a></th>
        <th><a href="?sort=lastchange">Last modified</a></th>
        <th>&nbsp;</th>
    </tr>
    
<tr class="parity0">
<td><a href="/hg/~anttip/ec168/suspend/">suspend</a></td>
<td>suspend development repository</td>
<td>Antti Palosaari</td>
<td class="age">2009-09-20</td>
<td class="indexlinks"><a  href="/hg/~anttip/ec168/suspend/archive/tip.zip">&nbsp;&darr;zip</a><a   href="/hg/~anttip/ec168/suspend/archive/tip.tar.gz">&nbsp;&darr;gz</a><a   href="/hg/~anttip/ec168/suspend/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity1">
<td><a href="/hg/~anttip/ec168/rtl2831u/">rtl2831u</a></td>
<td>rtl2831u development repository</td>
<td>Antti Palosaari</td>
<td class="age">23 months ago</td>
<td class="indexlinks"><a  href="/hg/~anttip/ec168/rtl2831u/archive/tip.zip">&nbsp;&darr;zip</a><a   href="/hg/~anttip/ec168/rtl2831u/archive/tip.tar.gz">&nbsp;&darr;gz</a><a   href="/hg/~anttip/ec168/rtl2831u/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity0">
<td><a href="/hg/~anttip/ec168/rtl2831u_4/">rtl2831u_4</a></td>
<td>rtl2831u development repository</td>
<td>Antti Palosaari</td>
<td class="age">2009-08-26</td>
<td class="indexlinks"><a  href="/hg/~anttip/ec168/rtl2831u_4/archive/tip.zip">&nbsp;&darr;zip</a><a   href="/hg/~anttip/ec168/rtl2831u_4/archive/tip.tar.gz">&nbsp;&darr;gz</a><a   href="/hg/~anttip/ec168/rtl2831u_4/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity1">
<td><a href="/hg/~anttip/ec168/qt1010/">qt1010</a></td>
<td>qt1010 development repository</td>
<td>Antti Palosaari</td>
<td class="age">2010-01-12</td>
<td class="indexlinks"><a  href="/hg/~anttip/ec168/qt1010/archive/tip.zip">&nbsp;&darr;zip</a><a   href="/hg/~anttip/ec168/qt1010/archive/tip.tar.gz">&nbsp;&darr;gz</a><a   href="/hg/~anttip/ec168/qt1010/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity0">
<td><a href="/hg/~anttip/ec168/rtl2831u_qt1010/">rtl2831u_qt1010</a></td>
<td>rtl2831u_qt1010 development repository</td>
<td>Antti Palosaari</td>
<td class="age">2010-02-16</td>
<td class="indexlinks"><a  href="/hg/~anttip/ec168/rtl2831u_qt1010/archive/tip.zip">&nbsp;&darr;zip</a><a   href="/hg/~anttip/ec168/rtl2831u_qt1010/archive/tip.tar.gz">&nbsp;&darr;gz</a><a   href="/hg/~anttip/ec168/rtl2831u_qt1010/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

<tr class="parity1">
<td><a href="/hg/~anttip/ec168/rtl2831u_3/">rtl2831u_3</a></td>
<td>unknown</td>
<td>unknown</td>
<td class="age">2009-08-25</td>
<td class="indexlinks"><a  href="/hg/~anttip/ec168/rtl2831u_3/archive/tip.zip">&nbsp;&darr;zip</a><a   href="/hg/~anttip/ec168/rtl2831u_3/archive/tip.tar.gz">&nbsp;&darr;gz</a><a   href="/hg/~anttip/ec168/rtl2831u_3/archive/tip.tar.bz2">&nbsp;&darr;bz2</a></td>
</tr>

</table>
</div>
</div>


</body>
</html>


---%<---
!
as a result no ec168 folder is made for me to install the DVB core moduoles from

Many thanks

---

### Post by size_XXM on 2012-04-18
See [http://linuxtv.org/hg/~anttip](http://linuxtv.org/hg/~anttip)
The "ec168" branch seems to no longer exist. Perhaps it was merged to main linuxtv branch, maybe even mainline Linux kernel?

---

