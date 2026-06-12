---
title: "Lost ability to convert WMF graphics after upgrade to 11.04"
date: 2011-07-12
forum: Multimedia Software
---

### Post by nlippincott on 2011-07-12
I have a very large graphics library that I use regularly, but all files are in WMF format. Prior to upgrading to Ubuntu 11.04 (was previously on 10.04), these files would preview in Nautilus, and GIMP would automatically convert them when they were opened.

Now, these files no longer preview in Nautilus, nor do they open and convert in GIMP. Package libwmf0.2-7 is installed.

Any suggestions? :confused:

---

### Post by nlippincott on 2011-07-12
More info...

I installed package libwmf-bin, so as to attain the command line utility "wmf2svg".

When I try to convert a file with wmf2svg, I get:

wmf_ipa_font_map: failed to load *any* font!

I am finding references on Launchpad that this is a bug introduced in Maverick. Am I sunk? ](*,)

---

### Post by d+r_4ever on 2011-09-28
> **nlippincott said:**
> I have a very large graphics library that I use regularly, but all files are in WMF format. Prior to upgrading to Ubuntu 11.04 (was previously on 10.04), these files would preview in Nautilus, and GIMP would automatically convert them when they were opened. 

Now, these files no longer preview in Nautilus, nor do they open and convert in GIMP. Package libwmf0.2-7 is installed.

Any suggestions? :confused:

I'm interested in a solution for this too! I used Irfanview in Windows before I switched to Ubuntu. Now I don't know how to convert my .wmf images. -R

---

### Post by d+r_4ever on 2011-09-28
I just saw this thread. I'm new to command line, so I didn't follow all of it, but it looks like it may be related and helpful? -R

[http://ubuntuforums.org/showthread.php?t=1688462&highlight=.wmf](http://ubuntuforums.org/showthread.php?t=1688462&highlight=.wmf)

---

### Post by Paddy Landau on 2012-05-19
I have raised a further bug report for this.

If it affects you, please [vote for the bug]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1001570") (green writing at the top-left of the page).

---

