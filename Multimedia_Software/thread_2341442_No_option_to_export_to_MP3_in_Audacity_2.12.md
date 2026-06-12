---
title: "No option to export to MP3 in Audacity 2.12"
date: 2016-10-28
forum: Multimedia Software
---

### Post by mark6006 on 2016-10-28
In my install of Audacity 2.12 I have many format options from which to choose for when I export an audio track - but no mp3 ([see screenshot]("https://www.dropbox.com/s/f6lzcnxe5594vk9/audacity-missing-mp3-option.jpg?dl=0")).

I've already done:
sudo apt-get install lame libmp3lame0
sudo apt-get install ubuntu-restricted-extras

Note that on linux there is no Libraries tab in Edit->Preferences where you would select the lame library (like there is in Windows). Its supposed to be dynamically found in Linux. I've done my research and would greatly appreciate any help in this. I have an older version of ubuntu on a different PC and its (older) version of Audacity 2.0x has the MP3 format available for exporting audio. However, that version of Audacity doesn't have the separate dropdown list selections of Header and Encoding as my current 2.12 version has (as the screenshot shows).


thanks -
[IMG]https://www.dropbox.com/s/f6lzcnxe5594vk9/audacity-missing-mp3-option.jpg?dl=0[/IMG]

---

### Post by vasa1 on 2016-10-28
1: please try to use the forum's image upload provision (the paper clip)
2: please post the output of ```
apt-cache policy audacity
```

I have Audacity 2.1.2-1 and can export to mp3.

```
$ apt-cache policy lame libmp3lame0
lame:
  Installed: 3.99.5+repack1-9build1
  Candidate: 3.99.5+repack1-9build1
  Version table:
 *** 3.99.5+repack1-9build1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
libmp3lame0:
  Installed: 3.99.5+repack1-9build1
  Candidate: 3.99.5+repack1-9build1
  Version table:
 *** 3.99.5+repack1-9build1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
$
```

---

### Post by mc4man on 2016-10-28
> **vasa1 said:**
> 

I have Audacity 2.1.2-1 and can export to mp3.


The op is looking under the "Other uncompressed files" export format. Whether mp3 is suppose to be there don't know, i'd file an issue upstream with audacity to ck. (the online user manual is noncommittal on this

---

### Post by mark6006 on 2016-10-28
```
[ATTACH=CONFIG]271829[/ATTACH]
```

apt-cache policy audacity
audacity:
  Installed: 2.1.2-1
  Candidate: 2.1.2-1
  Version table:
 *** 2.1.2-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by mark6006 on 2016-10-28
Thank you. Now solved. That unlabeled(!) dropdown list with "Other uncompressed files" selected that you mention was where I found MP3! For some reason, by default, it has "Other uncompressed files" selected which causes the two Header and Encoding dropdown lists to appear. But MP3 will not be found in Encoding and that was where I was incorrectly looking. Again, MP3 can instead be found in that 3rd dropdown list and replaces those Header & Encoding dropdown lists with MP3 option selections. 

Now I feel dumb. But I thank both responders mightily.:P

---

