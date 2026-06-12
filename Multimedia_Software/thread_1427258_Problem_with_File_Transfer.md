---
title: "Problem with File Transfer"
date: 2010-03-11
forum: Multimedia Software
---

### Post by Normund on 2010-03-11
Hello!
Got a problem, Search Tool didn't find any similar entries already posted.
Description in short. I use Ubuntu 9.10 (*Karmic Koala*). All updates have been installed promptly. PC's working as it should, *except* *for file transfer* to external Memory Stick, CF, SD, SC - you name it - cards. Smaller files get transferred easily, but anything as large as 50, 70 or 100 MB or more halts the process of transfer right in the middle of it. At times, if the memory card is new, the process is completed in a few minutes' time (I checked how long the transfer would take on a PC powered by Windows, with similar RAM and other specifications: 45 secs for a 130 MB file), but even with a speedy external volume of 1 TB the process of file transfer takes a a lot of time. Even when the files are copied smoothly, there appear to be halts in the process.

---

### Post by solar george on 2010-03-11
These halts are due to the fact that ubuntu buffers reads/writes made to external media to reduce the wear on flash drives, once the buffers are full they have to be written to the disks making it appear that the transfer has halted - this is why its especially important to make sure you eject/"Safely Remove" external drives under linux.

---

