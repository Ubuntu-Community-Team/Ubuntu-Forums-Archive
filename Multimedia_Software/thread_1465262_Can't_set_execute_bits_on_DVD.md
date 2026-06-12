---
title: "Can't set execute bits on DVD"
date: 2010-04-29
forum: Multimedia Software
---

### Post by aixwiz on 2010-04-29
I've run into a problem using K3B to write files to a DVD-RW (UDF format).  One file I'm writing to the DVD-RW is a shell script that needs to have the permission bits set to 555 (r-xr-xr-x).  The script needs to be able to run directly from the disc, so I set the scripts permissions to 555 on the original file.  When K3B writes the script to the DVD-RW, the permissions are always set to 444 (r--r--r--).

I've tried a few tests and found that I can write the script to a CD-RW and the permissions are set to 555.  The script runs fine from the CD-RW.  Unfortunately, I can't use a CD-R/RW for this project as one tar file this script deals with is larger than 2GB (that's why I'm using UDF).  Has anyone else seen this issue?  Any suggestions?

---

