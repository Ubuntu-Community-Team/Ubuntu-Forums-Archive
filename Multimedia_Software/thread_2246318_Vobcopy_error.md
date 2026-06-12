---
title: "Vobcopy error"
date: 2014-09-29
forum: Multimedia Software
---

### Post by aaron50 on 2014-09-29
Hi all,

i have been ripping dvd's on my headless ubuntu 14.04 box using vobcopy. I have about 100 dvd's I am starting with. My steps are as follows.
1.) insert the dvd
2.) sudo mount /dev/sr0 /mnt/cdrom
3.) vobcopy -f -l -m -o /ExternalMedia/Media/Movies -t nameofmovie
4.) sudo umount /mnt/cdrom 
and repeat with another dvd.

i was able to rip about 90 out of the first 100 perfectly fine and they look really nice when I play them on vlc from my microsoft laptop (menus and everything).

i am getting the same error with all of the others and I have done a lot of research and can't figure out what is going on. Here is what is happening:

1.) insert dvd
receive this error:
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]end_request: I/O error, dev sr0, sector 4096[/FONT]
Buffer I/O error on device sr0, logical block 512
[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]end_request: I/O error, dev sr0, sector 4096
[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Buffer I/O error on device sr0, logical block 512

[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]2.) sudo mount /dev/sr0 /mnt/cdrom
same error as above

3.) [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]vobcopy -f -l -m -o /ExternalMedia/Media/Movies -t nameofmovie
it goes through its normal rip language identifying the titles and angles etc. then rips the first few vob's then it gives me this error repeated and I cannot get out of the loop without rebooting the computer manually by holding the power button. The error is:
[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]end_request: I/O error, dev sr0, sector 7805312
Buffer I/O error on device sr0, logical block 1951328
[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Buffer I/O error on device sr0, logical block 1951329
[/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]end_request: I/O error, dev sr0, sector 7805312

and it just keeps repeating. I noticed it is happening with a lot of the newer DVDs. Does anyone have a solution for me? 

Thanks in advance[/FONT]

---

### Post by TheFu on 2014-09-30
There is no solution with vobcopy.

Newer, more popular DVDs, use broken  DVD formating as copy protection methods. Different sectors are specifically broken in the mastering design. There are commercial DVD rippers which claim to get around this - I think they have a DB of all the bad sectors for any commercial DVDs and know to skip those.

You can google to see more information on this and to find which programs make the claim.

---

### Post by aaron50 on 2014-10-02
Thank you for your input. Is there a better way than vobcopy to rip the full DVD that is free? One that can rip these troubled dvd's?

---

### Post by TheFu on 2014-10-02
> **aaron50 said:**
> Thank you for your input. Is there a better way than vobcopy to rip the full DVD that is free? One that can rip these troubled dvd's?

Not that I am aware of.  Every non-commercial solution will run into the same issues with by-design broken DVDs. THAT is the copy protection.

However, if you like, you might try using ddrescue to copy the DVD bit-for-bit to an ISO on a HDD, then point vobcopy at that copy.  Don't think this will work, but you can try it.

Must be nice to live in a place that doing this isn't illegal.

---

