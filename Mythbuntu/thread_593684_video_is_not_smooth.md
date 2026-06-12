---
title: "video is not smooth"
date: 2007-10-27
forum: Mythbuntu
---

### Post by meanmrmustard on 2007-10-27
I have the rc1 version output to a tv and have noticed that the video is not smooth while watching live tv with no other jobs running. It's barely noticable, but enough so to be irritating.

The video card is an Nvidia GeForce FX5200 with an Athlon XP 2500+ proc and 768 MB of RAM. 
I previously had this machine running Knoppmyth and never saw this behavior so I think it's unlikely that it's a hardware issue. 

Any ideas on what I might looks at to resolve this?

I'm also wondering if there's any difference in running aptitude update and upgrade as compared to installing the final version fresh.

---

### Post by Lem on 2007-10-27
I have a similar spec that runs perfect. Have you installed the nvidia drivers? (nvidia-glx-new) and run nvidia-xconfig?

---

### Post by Lem on 2007-10-27
Also try tinkering with your deinterlace settings. Kernel & Bob tend to work well to minimise jitter.

I'm running an alpha that's been upgraded and things seem fine.

---

### Post by meanmrmustard on 2007-10-28
Yes I have the Nvidia drivers.
I have tried every combination of deinterlace algorithm and MPEG decoder, nothing even slightly improves the jitter.

---

### Post by CaptainPatent on 2007-10-28
What kind of tuner card do you have? I've been having a similar problem and I think it's due to my ATI TV Wonder 200. I have lower hardware specs, but plenty to be sufficient for a MythTV box.

---

### Post by meanmrmustard on 2007-10-28
I've got a PVR 500 and one 250 in the box.
I've been thinking I could put a better video card in to see if it will make a difference.

---

### Post by axelsvag on 2007-10-29
I use the 500PVR aswell, and noticed this in the RC, it was much better when I changed to final release instead of updating the RC. In my case it seemed like the videodriver was not happy with my installation.

---

### Post by meanmrmustard on 2007-10-30
I was about to re-install from a newly downloaded/burned cd of the final version, but first  I ran 'dpkg-reconfigure xserver-xorg' and set my resolution to 600x800 - after reading a page of the Knoppmyth wiki - and the jitter has stopped.

---

