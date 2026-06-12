---
title: "Acquiring the xc3028 firmware file for Kworld 120"
date: 2009-01-25
forum: Mythbuntu
---

### Post by Jimbo13 on 2009-01-25
I'm a linux novice but I usually RTFM and don't have many problems.

I been following the directions found on [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120) to set my tuner card.

```
# In order to use, you need to:
#       1) Download the windows driver with something like:
#               wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
#       2) Extract the file hcw85bda.sys from the zip into the current dir:
#               unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
#       3) run the script:
#               ./extract_xc3028.pl
#       4) copy the generated file:
#               cp xc3028-v27.fw /lib/firmware

```

I get to step 3 and receive the following error.

```
administrator@ubuntu:/usr/src/linux-headers-2.6.27-9/Documentation/video4linux$ ./extract_xc3028.pl
bash: ./extract_xc3028.pl: Permission denied
administrator@ubuntu:/usr/src/linux-headers-2.6.27-9/Documentation/video4linux$ sudo ./extract_xc3028.pl
[sudo] password for administrator: 
sudo: ./extract_xc3028.pl: command not found
```


I believe I am on the right track but for some reason beyond my understanding the perl script isn't running.  I can see the extract_xc3028.pl file in the correct directory when I attempt to run it.

I'm on intrepid Mythbuntu build and according to the wiki entry have the latest V4L-DVB repository.

Any ideas? Thanks.

---

### Post by ian dobson on 2009-01-25
Hi,

Try:-

```

cd /tmp
wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
sudo chmod +x /usr/src/linux-headers-2.6.27-9/Documentation/video4linux/extract_xc3028.pl
/usr/src/linux-headers-2.6.27-9/Documentation/video4linux/extract_xc3028.pl
sudo cp xc3028-v27.fw /lib/firmware

```

This will download the firmware,extract it to /tmp then copy it to your firmware directory. Rather than extracting it to the linux source directory (bad idea).

you shouldn't need root to extract the firmware, only to copy it to the correct directory.

Regards
Ian Dobson

---

### Post by renaud.s on 2009-06-23
You may have find the solution already but I had the same issue and that' what I did...

Simply check the rights of the .pl script, it must be executable (x).

Hope this helps...

---

### Post by AboveTheLogic on 2009-06-24
alternatively, you may run these commands in the working directory

sudo chmod 755 extract_xc3028.pl
sudo chmod +x extract_xc3028.pl

then try
./extract_xc3028.pl

---

