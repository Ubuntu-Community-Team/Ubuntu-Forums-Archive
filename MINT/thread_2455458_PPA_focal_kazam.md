---
title: "PPA focal kazam"
date: 2020-12-20
forum: MINT
---

### Post by Kevin McCready on 2020-12-20
I'm trying to install kazam but it doesn't install with PPA in the latest version of Mint. Is there a way to do it? Or is there a better video screen capture program?

DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=20
DISTRIB_CODENAME=ulyana
DISTRIB_DESCRIPTION="Linux Mint 20 Ulyana"
NAME="Linux Mint"
VERSION="20 (Ulyana)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 20"
VERSION_ID="20"
HOME_URL="https://www.linuxmint.com/"
SUPPORT_URL="https://forums.linuxmint.com/"
BUG_REPORT_URL="http://linuxmint-troubleshooting-guide.readthedocs.io/en/latest/"
PRIVACY_POLICY_URL="https://www.linuxmint.com/"
VERSION_CODENAME=ulyana
UBUNTU_CODENAME=focal

---

### Post by howefield on 2020-12-20
Thread moved to the "*MINT*" forum.

PS. You know better, so please put your questions in the correct sub forum in future.

---

### Post by ajgreeny on 2020-12-20
Which PPA have you enabled?
There are many PPAs that have packages only for much older versions of Ubuntu, and hence Mint, but the PPA I have found but never used is [https://launchpad.net/~sylvain-pineau/+archive/ubuntu/kazam?field.series_filter=focal](https://launchpad.net/~sylvain-pineau/+archive/ubuntu/kazam?field.series_filter=focal)
Is that the one you used?

You can easily use ffmpeg to create screen captures, which I have used in the past, and being ffmpeg there are more available options than anyone is ever likely to need.
The very simple script I started using a few years ago and which could easily be updated or upgraded as you want, depending on the output filetype you want and resolution of the output file is shown below as the script, named rmd (Record My Desktop)
```
#!/bin/bash
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x1080 -i :0.0 -acodec flac -vcodec libx264 -threads 0 ./Desktop/mydesktop.mkv 

```

---

### Post by T6&amp;sfpER35% on 2020-12-20
i used kazam before but found that the output would be blurry and the mouse pointer wouldn't show properly.
changed to [simplescreenrecorder&#8203;]("https://www.ihaveapc.com/2020/12/record-screen-in-linux-mint-with-simplescreenrecorder/") which works beautifully.
not sure if it works in mint 20 though,it should

---

