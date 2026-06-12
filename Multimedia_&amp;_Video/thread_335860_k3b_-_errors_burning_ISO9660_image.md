---
title: "k3b - errors burning ISO9660 image"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by domz76 on 2007-01-10
Hi, im using k9copy to rip/shrink a DVD9 to 4gb DVD5, size. This creates the usual video_ts and audio folders with the correct VOBs inside as expected. I've tried playing the vobs through VLC player to test the quality - all good.

The problem is when I burn the structure (adding the VOBs etc) to DVD using k3b, or burn an ISO9660 image (previously created in k3b using the VOBs as above, and tested - the ISO plays fine) to DVD.

The burn brocces appears to go through Ok, but the result is a disk that cannot be read EVERY time. I've tried setting the option to 'verify written data' which reports that all data written matches the MD5 sums (i.e. no errors)

Incidentally the writing speed (set to auto) is quoted as 'started as 12.5x', but the estimated speed is more like 6x. The only other option from the drop-down is 2x (this is obviously way too slow - my disks are 8x rated, and the burner is 16x) In any case i don't think that the speeds are the issue here.

Ive also checked on google that the best supported format for optical disks is UDF as apposed to ISO9660 (outdated?). Is there any way to specify UDF as an output format??

Am I doing anything wrong???? Is it because im using a USB burner? Do i need to make any configs for the burner?

-----------------------
My specs:
Ubuntu Edgy 6.10 (i386)
external USB2 DVD writer (reports as HL-DT-ST DVDRAM GSA-4120B)
-----------------------

Thanks in advance for your help!

---

