---
title: "Problems with PPTP VPN in Intrepid"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by Devo66 on 2009-03-13
I apologize if this has been discussed already, but searching didn't turn anything up. 

Trying to connect to a Linksys RV082 using PPTP under Intrepid.    

It works fine if I turn MPPE encryption off, but if I use MPPE, I get 50% packet loss when pinging through the VPN.  During that pinging, my /var/log/syslog file is spitting out the following:

mppe_decompress[0]: FLUSHED bit not set in stateless mode!

I'm connecting with Network Manager.  Any thoughts?

---

### Post by Devo66 on 2009-04-09
Bump.  Doesn't anybody have any idea on this?  I hate having to use Windows to connect to my VPN.

---

### Post by white_hat on 2010-03-10
same problem with me :(
changing MTU doesn't help

---

### Post by .James.H. on 2010-03-28
I'm not sure, but this appears to be a bug in src/drivers/net/ppp_mppe.c

While reading the MPPE RFC, I learned that the FLUSHED bit shall be set when ENCRYPTED is enabled.  Sure enough I found this in ppp_mppe.c:
```

/*
 * Note that even though we have initialized the key table, we don't
 * set the FLUSHED bit.  This is contrary to RFC 3078, sec. 3.1.
 */
state->bits = MPPE_BIT_ENCRYPTED;

```MPPE_BIT_FLUSHED is conspicuously absent from these lines of code.  This is apparently intentional as the comment indicates but goes without further explanation.  There may indeed be a good reason for this but I don't know what it could be.

I have fixed this by assuming the reason is valid, and disabled the code that does a sanity check on the FLUSHED bit in stateless mode.  I have also confirmed that the tunnel still works correctly after this change.

Remove the following code from the mppe_decompress function body in file ppp_mppe.c:
```

if (!state->stateful && !flushed) {
    printk(KERN_DEBUG "mppe_decompress[%d]: FLUSHED bit not set in "
           "stateless mode!\n", state->unit);
    state->sanity_errors += 100;
    sanity = 1;
}

```Now build and install the new module.  This process leaves the old module intact in case you want to go back to it.  Just change the ppp_mppe.ko symlink to point back to the old module.

```

cd /usr/src/$KERNEL/drivers/net
mv Makefile Makefile.orig
echo 'obj-$(CONFIG_PPP_MPPE) += ppp_mppe.o' > Makefile
make -C /lib/modules/2.6.27-17-generic/build M=$(pwd) modules
mv Makefile.orig Makefile
rmmod ppp_mppe
cp ./ppp_mppe.ko /lib/modules/$KERNEL/kernel/drivers/net/ppp_mppe.ko-new
cd /lib/modules/$KERNEL/kernel/drivers
mv ppp_mppe.ko ppp_mppe.ko-old
ln -s ppp_mppe.ko-new ppp_mppe.ko
modprobe ppp_mppe

```I confirmed the fix by writing a 10-megabyte random file locally, copying it across the tunnel using scp, and performing sha1sum on the file at both ends.  The hashes matched, so I conclude the tunnel is not dropping or corrupting data.

---

### Post by Andre_44 on 2010-08-23
I'm trying this fix right now, I'll post back here if i have any success.

---

### Post by Andre_44 on 2010-08-23
The patch worked perfectly. this needs to go upstream, .James.H. Have you considered filing a bug report?

---

### Post by phord2 on 2011-11-22
Curious.  I have the same problem in Oneiric, and this patch fixed it there, too.

Background: I was able to connect to one corporate PPTP server without any problem.  But when connected to another corporate server, I receive about every other packet with the FLUSHED bit turned off.  These packets are dropped by the stock driver just like the SPEC says they should be.  But when I stop dropping those packets (by making this change to the driver), the problem went away.

I could see the symptom clearly by pinging a machine on the VPN.  Every other ping packet is lost with the old driver.  Once I installed the new driver, every ping is responded correctly.

Phil

---

### Post by Tiftof on 2011-12-02
Same problem here and the same fix solves it. The vpn connection is provided by a USR8200 VPN.

Is the problem related to the USR8200 not setting the flushed bit (because it "forgot" to set it or because it didn't initialize the key table while it should during stateless encryption) or because of the linux driver not setting the flushed bit in the code as said by James.H ?

---

### Post by .James.H. on 2011-12-16
I'm glad this is proving helpful to others.  We've been using it ever since I posted my "fix" without any issues.


I don't really know how to push this information upstream or anything - anyone who has the know-how and inclination PLEASE feel free to do so on my behalf.  This has surely annoyed far more people than we see in this thread. :)

---

