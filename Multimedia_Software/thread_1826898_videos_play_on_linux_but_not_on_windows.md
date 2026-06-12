---
title: "videos play on linux but not on windows?"
date: 2011-08-17
forum: Multimedia Software
---

### Post by crave420fubar on 2011-08-17
I had a DSM-G600 (D-Link home ftp server rev B) that... well maybe dead. I wanted to save the data on another FTP server (windows based... don"t hurt me) So I connected the PATA drive via USB to one of my Linux/hybrid machines mounted the file system and started to transfer files from the USB drive to a storage partition and later transfered some video files to the ftp server. After I transfered the video files to the server I found that windows was unable to play the files at all. The file size also appears to be just short of what it should be.

the source disk is EXT 2
The files do play on the machine.
I have duplicates of the files in question on the windows based machine and never had a problem.
Linux machine is formated in EXT 3
I believe that the files are mainly or all AVI

I attempted to do a Google search and waisted about 3 hours without even a close issue. 

I changed the permissions under root to my user and still had same problem.
Please not that I do have duplicates of the same files so I am not concerned about losing data ;) I was backing up an old backup that I had already backed-up.

Suggestions?

---

### Post by smurphy_it on 2011-08-17
Check the .avi files in Windows Media Player (properties) to see the video properties.  I would probably say you don't have the proper codecs installed on the windows side.

Perhaps you should start with downloading the "Xvid Codec for Windows".  You can get that from: [http://www.xvid.org/Downloads.15.0.html](http://www.xvid.org/Downloads.15.0.html)

On your linux machine, you can determine the video codec involved and what not using file.

Here is an example:
```
file myvideo.avi
```

Sample output:

myvideo.avi: RIFF (little-endian) data, AVI, 704 x 384, 23.98 fps, video: XviD, audio: Dolby AC3 (6 channels, 48000 Hz)

---

### Post by crave420fubar on 2011-08-17
Thanks for the response. However I have discovered that it is either a network issue or an ftp client issue. I determined this by connecting the drive to my windows based POS (Positively Obsolete Server) and using DiskInternal Linux Reader the files play just fine.

I do not know the cause at this time. I'm leaning toward the Linux version of the Firefox addon FireFTP.

I would ask the admin who sees this to move this thread to a networking issues area.

---

### Post by smurphy_it on 2011-08-18
You could try a full fledged FTP client (like filezilla).  Additionally, by utilitizing CRC-checksums, you can determine if the file is "fully intact".

One would run a crc-check on the file, and save the MD5 hash (or SHA-1 hash) in a plain text file, and transfer it with the file.  On the windows site, run an utility for comparing the hash.

---

