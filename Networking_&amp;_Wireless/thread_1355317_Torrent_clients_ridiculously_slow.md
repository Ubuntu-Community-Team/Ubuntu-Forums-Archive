---
title: "Torrent clients ridiculously slow"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by Dookert on 2009-12-14
This has been addressed in a few other forum spots but none have helped me. I tired opening port 6881 which was suggested as a fix through the command line. no dice. I have made sure all ports are forwarded through my router and tried 4 different clients. ALL of them will not download anything over 50 and change kb/s. like they hover around 50-60 kb/s. no limits are set for download or upload speeds yet my freakin' computer will upload at 500Kb/s like it is right now. currently deluge is downloading at 20kbs and uploading 450kb/s WTF! I have also increased amount of seeders aloud, all that stuff.

I really like ubuntu, so much cleaner than windows, everything just WORKS, except for this. Please help, I download a lot and if I cant get this to work, sadly, im switching back to XP:( I just cant spend 3 days downloading 700 mb files.

---

### Post by Dookert on 2009-12-14
consequently, bitlord, on XP flies. like absolutely screws. The current file im downloading on deluge has 240 seeders, and im getting 20kbs? WTF! while the same file on windows is bolting at over a meg a second.

---

### Post by cenzorrll on 2009-12-14
try capping your upload speed, often times when you are uploading at max speed the download speed suffers,  i've foung that limiting the upload speed to about 50-75% max optimizes download speeds.  you may also want to make sure the torrents you're trying to download have a good seed/peer ratio.

other fixes may be increasing the number of possible connections, making sure a firewall isn't blocking your port. most torrent clients have a button that tests to make sure your port is forwarded correctly, use that and if it is, then the slow speeds are most likely due to seed/peer ratio, and number of seeds.

---

### Post by FrnchPrss on 2009-12-15
Dookert,
Are you trying to download through your wifi connection?

If so have you checked your reported Bit Rate from iwconfig?
Also check
[https://answers.launchpad.net/ubuntu/+source/wireless-tools/+question/30772](https://answers.launchpad.net/ubuntu/+source/wireless-tools/+question/30772)

---

