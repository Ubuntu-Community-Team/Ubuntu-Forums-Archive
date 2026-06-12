---
title: "dvd+rw write failed: would cross 4 gig boundary"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by mvsjes2 on 2007-05-15
I have a script that I use to backup partimage files to dvd. Partimage chops its image into 2 gig files and I take each one and write a new session to the dvd, the theory being if I run out of space I can have the user pop in a fresh dvd and continue writing.

I was writting to a dual-layer dvd and got a funny error message. I was hoping someone could explain it to me.

Backing up /mnt/sda7/partimages/2007-05-15/sda5-image.gz.002 (size 1430634594)
Backup size requested: 1430634594, available on dvd: 2832662528.
growisofs -M /dev/dvd  -R /mnt/sda7/partimages/2007-05-15/sda5-image.gz.002
*:-( next session would cross 4GB boundary, aborting...*

The space available on dvd was reported by dvd+rw-mediainfo. Since it's a dual-layer dvd the "4 gig boundary" should be immaterial, right?

I did see this:
DVD+R DOUBLE LAYER BOUNDARY INFORMATION:
 L0 Data Zone Capacity: 2086912*2KB, can no longer be set
but I'm not sure what it means.

Here's the output from dvd+rw-mediainfo:
INQUIRY:                [HL-DT-ST][DVDRAM GSA-H10N ][JL10]
GET [CURRENT] CONFIGURATION:
* Mounted Media:         2Bh, DVD+R Double Layer*
 Current Write Speed:   2.4x1385=3324KB/s
 Write Speed #0:        2.4x1385=3324KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     2.4x1385=3324KB/s@[0 -> 4173823]
 Speed Descriptor#0:    02/4173823 R@4.9x1385=6853KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Media ID:              RITEK/D01
 Legacy lead-out at:    2086912*2KB=4273995776
DVD+R DOUBLE LAYER BOUNDARY INFORMATION:
 L0 Data Zone Capacity: 2086912*2KB, can no longer be set
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    5
 State of Last Session: empty
 "Next" Track:          5
 Number of Tracks:      5
READ TRACK INFORMATION[#1]:
 Track State:           partial/complete
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            192*2KB
READ TRACK INFORMATION[#2]:
 Track State:           partial/complete
 Track Start Address:   2240*2KB
 Free Blocks:           0*2KB
 Track Size:            695232*2KB
READ TRACK INFORMATION[#3]:
 Track State:           partial/complete
 Track Start Address:   699520*2KB
 Free Blocks:           0*2KB
 Track Size:            1043520*2KB
READ TRACK INFORMATION[#4]:
 Track State:           partial/complete
 Track Start Address:   1745088*2KB
 Free Blocks:           0*2KB
 Track Size:            1043552*2KB
READ TRACK INFORMATION[#5]:
 Track State:           blank
 Track Start Address:   2790688*2KB
 Next Writable Address: 2790688*2KB
* Free Blocks:           1383136*2KB*
 Track Size:            1383136*2KB
FABRICATED TOC:
 Track#1  :             14@0
 Track#2  :             14@2240
 Track#3  :             14@699520
 Track#4  :             14@1745088
 Track#AA :             14@2788640
 Multi-session Info:    #4@1745088
READ CAPACITY:          2788640*2048=5711134720

---

### Post by mvsjes2 on 2007-05-15
Sorry, I should have done more reading before I posted. It looks like dual layer burning is more complicated than I thought.

Apparently you have to add -use-the-force-luke=4gms to the growisofs command if you have a modern kernel and can allow directories be located >4gig when burning new sessions.

If you google this parm you will see lots of info.

---

### Post by mvsjes2 on 2007-05-15
Not so solved.

I reran this using the use-the-force-luke thingy and it still gave me the same error.

I read that a kernel patch is required in order to use this switch, but in other places it says the patch is only necessary if your kernel is < 2.6.8. I'm on feisty so this shouldn't be required.

Can anyone help me with this?

---

### Post by sqbaillie on 2007-10-16
Is there any progress on a solution for this issue?

I'm getting the same problem on Feisty when adding sessions to a 25GB Sony BD-RE disc.  I'm running:

  # growisofs -M /dev/dvdrw -R -J -joliet-long -use-the-force-luke=4gms -root /mirror/backup/ccarenhs/backup /mirror/backup/ccarenhs/backup
:-( next session would cross 4GB boundary, aborting...

  Package: dvd+rw-tools
  Version: 7.0-6

---

### Post by arnold_mad on 2007-11-29
Does anyone have a solution for the problem with the BD drive ?

---

