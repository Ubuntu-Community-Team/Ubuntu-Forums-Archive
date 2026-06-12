---
title: "No sound on pavilion dv3000"
date: 2009-06-07
forum: Multimedia Software
---

### Post by gino on 2009-06-07
Hi,
Just installed Ubuntu 9.04 on a new pavilion laptop dv3000. Everything seems fine but there is no sound. Any advice on how to proceed? I will click, type commands, cut and paste, even read web pages. 
Please Help
:)

---

### Post by isparkes on 2009-10-27
I'm running Karmic and had the same problem, solved it by editing 

```
etc/modprobe.d/alsa-base.conf
```

and added the line

```
options snd-hda-intel model=hp-m4 enable_msi=1
```

After this, reboot, and all should be well.

My initial experiences with 9.10 (it's not even releases yet) have been very, very favourable. It's all working well, the only thing that does not is the fingerprint reader. But I use Blueproximity for that, and am more than happy with the solution.

---

### Post by Ulysses361 on 2009-10-28
Please execute step 1 and then send us output from step 3 and step 4 in the following procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

