---
title: "Handbrake on 24.04 how to get it going…"
date: 2024-10-11
forum: Multimedia Software
---

### Post by shantiq on 2024-10-11
After my upgrade from 22.04 to 24.04 I try to do DVD rip to archive one of my DVDs to my hard drive and then realised that handbrake had been wiped out so I had to bring it back also had to bring back libdvdcss2 Without which nothing would work so these are the steps I had to take if this is of any use to anyone else&#8230;






&#10122;```
sudo apt-get install libdvd-pkg



```


&#10123;```
sudo dpkg-reconfigure libdvd-pkg



```some question are asked here Yes is the answer




&#10124;To check libdvdcss2


```
apt-cache policy libdvdcss2

```libdvdcss2:
  Installed: 1.4.3-1~local
  Candidate: 1.4.3-1~local
  Version table:
 *** 1.4.3-1~local 100
        100 /var/lib/dpkg/status


[I]Install HandBrake:
[/I]

&#10125; ```
sudo add-apt-repository ppa:stebbins/handbrake-releases && sudo apt-get update && sudo apt-get install handbrake

```

To my understanding there is always a period with new version of Ubuntu LTS when the GTK is not yet released only the CLI thus far (I may be wrong on that)








AND now to archive:




&#10126; ```
HandBrakeCLI -i /dev/sr0 -o /home/shan/Videos/"Meet".mkv --main-feature  -a 1,3  -e ffmpeg2 -b 3000 -E copy  -r 30 -s "1,2,3"

```


Of course modify to your wishes  happy archiving ...

---

