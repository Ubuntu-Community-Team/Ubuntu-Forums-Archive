---
title: "Nvidia optimus gpu tearing in ubuntu session (compiz"
date: 2015-09-04
forum: Multimedia Software
---

### Post by mc4man on 2015-09-04
I've had optimus (nvidia mobile) gpu's in my laptops for quite some time but never used the nvidia gpu due to tearing everywhere.
Based on the comment here tried the suggestion & it removed almost all instances of tearing on a GeForce GT 755M using an _ubuntu session (unity/compiz_
[http://ubuntuforums.org/showthread.php?t=2293066&p=13349318&viewfull=1#post13349318](http://ubuntuforums.org/showthread.php?t=2293066&p=13349318&viewfull=1#post13349318)

Have tested with standard repo nvidia 346 drivers, the ppa 340 & 355. The later worked best here but all showed improvement.
The biggest issue is that every time _nvidia-prime_ switches     from using the Intel gpu to Nvidia a new xorg.conf is generated, this means re-editing, logging out/in every time.

To prevent that found out what (gpu-manager) regenerated the file & where it got the xorg.conf  'template' so to speak.
To that end a test ppa,_ trusty or vivid_, only tested here on an ubuntu session. To ck. just read page before using ppa, only the ubuntu-drivers-common package needs to be updated. (that's where the stuff is..
Also instruction on how to revert.
Comments on suitability & performance welcome
[https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test](https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test)

---

### Post by QIII on 2015-09-04
Hey!  Good job!

If you could put the bit about where gpu-manager gets the "template" for avoiding the xorg.conf problem in there I'm sure it would be appreciated so people understand what is going on when they use the PPA.

---

### Post by mc4man on 2015-09-04
When users switch between Intel & Nvidia,  gpu-manager, (from ubuntu-drivers-common) does stuff including removing or generating/regenerating xorg.conf.
Can be seen in /var/log/gpu-manager.log - 
> Intel hybrid system
Nvidia driver version 355.11 detected
[COLOR="#0000CD"]Removing xorg.conf. Path: /etc/X11/xorg.conf[/COLOR]
Powering off the discrete card
Unloading nvidia-uvm with "no" parameters
Unloading nvidia with "no" parameters


and the other way (to nvidia -
> can't access /etc/X11/xorg.conf
Check failed
Removing xorg.conf. Path: /etc/X11/xorg.conf
Moved /etc/X11/xorg.conf to /etc/X11/xorg.conf.09032015
[COLOR="#0000CD"]Regenerating xorg.conf. Path: /etc/X11/xorg.conf[/COLOR]
Powering on the discrete card
Loading nvidia with "no" parameters

The Intel gpu won't run with the nvidia xorg.conf, that's why it's removed when switching to Intel & recreated fresh when nvidia is enabled.

Turns out in /ubuntu-drivers-common-0.2.91.11/share/hybrid/gpu-manager.c there is a section that defines the xorg.conf to be created. So in the intel device section added the desired option. 

```
--- /ubuntu-drivers-common-0.2.91.11/share/hybrid/gpu-manager.c	2015-05-12 04:44:51.000000000 -0400
+++ /ubuntu-drivers-common-0.2.91.11.1/share/hybrid/gpu-manager.c	2015-09-03 23:57:23.779456000 -0400
@@ -1652,6 +1652,7 @@
                 "    Driver \"intel\"\n"
                 "    BusID \"PCI:%d@%d:%d:%d\"\n"
                 "    Option \"AccelMethod\" \"SNA\"\n"
+                "    Option \"TearFree\" \"True\"\n"
                 "EndSection\n\n"
                 "Section \"Screen\"\n"
                 "    Identifier \"intel\"\n"
```

That's about the logic of it.

---

### Post by mc4man on 2015-09-04
Here it seems that cursor movement in a video can cause some  tearing, very minor but does happen...
(tested on 15.04 with standard repo nvidia-346, worked ok so adding to ppa

Would be curious if any degrading or artifacts seen by using tear free in this manner.

edit: what's also interesting with 15.04 is ubuntu-drivers-common has broken out SNA from the Device config. It's still added as the default but it appears 15.04 version allows UXA somehow. Maybe something trusty could use, don't know. General section including vivid tear free patched

```
static bool write_prime_xorg_conf(struct device **devices, int cards_n) {
    int i;
    _cleanup_fclose_ FILE *file = NULL;
    _cleanup_free_ char *accel_method = NULL;

    switch (prime_intel_driver) {
    case MODESETTING:
        accel_method = strdup("");
        break;
    case UXA:
        accel_method = strdup("    Option \"AccelMethod\" \"UXA\"\n");
        break;
    default:
        accel_method = strdup("    Option \"AccelMethod\" \"SNA\"\n");
        break;
    }

    if (!accel_method) {
        fprintf(log_handle, "Error: failed to allocate accel_method.\n");
        return false;
    }

    fprintf(log_handle, "Regenerating xorg.conf. Path: %s\n", xorg_conf_file);

    file = fopen(xorg_conf_file, "w");
    if (file == NULL) {
        fprintf(log_handle, "I couldn't open %s for writing.\n",
                xorg_conf_file);
        return false;
    }

    fprintf(file,
            "Section \"ServerLayout\"\n"
            "    Identifier \"layout\"\n"
            "    Screen 0 \"nvidia\"\n"
            "    Inactive \"intel\"\n"
            "EndSection\n\n");

    for(i = 0; i < cards_n; i++) {
        if (devices[i]->vendor_id == INTEL) {
            fprintf(file,
                "Section \"Device\"\n"
                "    Identifier \"intel\"\n"
                "    Driver \"%s\"\n"
                "    BusID \"PCI:%d@%d:%d:%d\"\n"
                "    Option \"TearFree\" \"True\"\n"
                "%s"
                "EndSection\n\n"
```

---

### Post by mc4man on 2015-09-06
Tests here on my hardware show that this will have no effect on a 14.04.1 install with that releases default mesa stack. Tear Free is enabled, then immediately disabled, seen clearly in /var/log/Xorg.0.log.
Works fine in 14.04.3, 14.04.1 with the lts mesa packages & probably, (not tested) with 14.04.1 + Oibaf ppa

---

