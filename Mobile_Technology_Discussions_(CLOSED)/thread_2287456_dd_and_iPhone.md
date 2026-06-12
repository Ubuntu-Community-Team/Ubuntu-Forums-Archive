---
title: "dd and iPhone"
date: 2015-07-19
forum: Mobile Technology Discussions (CLOSED)
---

### Post by jbob0124 on 2015-07-19
I have an iPhone 6 (128GB) with iOS 8.1.4 (Jailbroken) for the use of Terminal and OpenSSH.  My phone had been disabled so I had to restore it as new, because of that  I am trying to create an IMG file so that I can extract the photos from it.  I have done it in the past successfully, but can't seem to get it done now.  I have been trying the following commands to extract an IMG.  Then use Photorec on the IMG.

```
dd if=/dev/disk0 | ssh <username>@<computer-ip> 'dd of=iphone.img'
```

also tried

```
ssh <username>@<phone-ip> dd if=/dev/rdisk0 bs=1M | dd of=iphone.img
```

When I run the commands in the terminal, I get the IMG file after about 4-5 hours and it says the size is 128GB.  After it has completed with the DD, I use:

```
photorec iphone.img
```

For some reason I don't seem to be getting any of my personal photos, just seems to be generic photos and only a few at best (20 or so).  Am I missing something within either of the DD comand or Photorec command?  I have also taken a few screen shots and a few pictures on the phone just to test it with the dump command, but those aren't showing up either.  Is it possible that I am not grabbing the right location or is there another step in-between the DD and Photorec?  Any help will be appreciated.

---

