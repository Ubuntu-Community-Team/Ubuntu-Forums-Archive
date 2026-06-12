---
title: "PVR-500 2nd tuner records blackness"
date: 2008-01-30
forum: Mythbuntu
---

### Post by dhjohnson on 2008-01-30
I recently had a Feisty MythTV frontend/backend but decided to upgrade to Mythbuntu Gutsy.  I have a Hauppauge PVR-500.  Since I've upgraded, my second tuner records only blackness or dark static.  The first tuner is fine.  IVTV seems to load fine and I've looked at some logs without seeing anything out of the ordinary.  I have a hunch that upgrading packages is breaking it.  Any hints?  :confused:

---

### Post by dhjohnson on 2008-01-31
Bump.

---

### Post by shad0w_walker on 2008-01-31
How are you trying out the second tuner? In myth or using a seperate program? It might be a weird config issue with Myth after the upgrade. Give it a try with something like mplayer and directly access the tuner to make sure its not something in the middle.

---

### Post by ian dobson on 2008-02-01
Hi,

It must be an upgrade issue. I have a PVR-500 in my backend at the moment (I had a PVR 150 during my testing) and don't have any problems.

Running 64Bit gusty on a Q6600.

Regards
Ian Dobson

Have you tried removing all the cards from the Myth setup then reinstalling them?

---

### Post by dhjohnson on 2008-02-04
I've played around with this a bit more, and have ruled out that it doesn't have anything to do with updating packages.  The symptom only manifests itself after MythTV attempts to record two shows at once.  I can watch TV on both tuners, but after two shows try to record at once, that second tuner only shows static.

---

### Post by dhjohnson on 2008-02-06
After yet another installation, this time only activating one tuner, I found that I was wrong again.  After recording a few shows on the tuner, mythtv started recording static.  This time I looked through kern.log, and found

```
Feb  6 20:03:16 mythtv kernel: [74151.382983] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
Feb  6 20:03:16 mythtv kernel: [74151.382992] ivtv0: Cause: the application is not reading fast enough.
```

Could this be related to LVM?

---

### Post by ian dobson on 2008-02-07
Hi,

Maybe try increasing the size of your ivtv mpeg buffers. There is a command line parameter to increase this value.

What through put are you getting from your drive(s) that your using for recording? On my MDADM raid 5 array with 4x500Gb I'm seeing about 90-95Mb/sec max write speed (measured with bonnie++), and I can record 2 channels at the same time without the system breaking out in a sweat.

Is your system heavly loaded? When recording 2 channels and watching a 3rd stream (on another computer) I see mythtvbackend using about 2-4% cpu (from TOP). Backend running on a Q6600 with 2Gb ram.

Regards
Ian Dobson

---

### Post by dhjohnson on 2008-02-07
Ian,

I'm not sure how to increase the size of the buffers in mythbuntu.  From what I've read thus far, the /etc/modprobe.conf file should be edited, but mythbuntu doesn't seem to have that.

---

### Post by ian dobson on 2008-02-07
Hi,

Have a look in the /etc/modprobe.d/options file, or just create a file called ivtv in the /etc/modprobe.d directory.

and add something like:-

options ivtv enc_mpg_buffers=8

to allocate 8 MB for the mpeg buffering. I think the default is 4Mb.

Regards
Ian Dobson

---

### Post by dhjohnson on 2008-02-07
Can/should I allocate more than 8MB?  What's the max?

---

### Post by ian dobson on 2008-02-07
Hi,

Suck it and see. Maybe try 8,16,32, I'm not sure how far you can go.

What specs. does your PC have?

Regards
Ian Dobson

---

