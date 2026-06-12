---
title: "Odd Samba behavior but in one direction only"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by pr0cs on 2009-11-20
I recently built a file server using 9.10 64bit and after some headaches (I may post my experience in the other forum/thread) I finally got everything up and running as I expected.
I enabled the Samba server but I'm getting some odd behavior.
I need to access my server from my Windows (XP/W7) machines on the network and with the W7 machine (I have not tried xp yet) I regularly get disconnections.

I have several large files that I need to copy from 1 Windows machine on the network to the samba share with 9.10.  If I use Windows to copy the file it will regularly disconnect, sometimes complete but often fail mid-way through the copy.

If I attempt the same thing on 9.10, so connect to the Windows machine's share and copy it works flawlessly.   Now I'm sure all you hardcore Ubuntu people are saying "i'm not surprised" :p  but still it would be nice to get some consistent behavior.

I didn't notice anything odd in samba logs, nothing that stood out.

If I use FTP from Windows->9.10 it works fine (albeit slow), at least doesn't disconnect.

Is there anything I could do to tweak Samba on the 9.10 side to encourage the connection to be more stable, there seems to be very limited (as usual) options on Windows to try and encourage the connection to not drop.

The connection to the share seems fine, just will occasionally drop saying "path/ connection has been lost", the file transfer fails but checking the connection seems to show the connection is still there.  So it sort of gave up during the transfer somehow.

Thanks for any hints you might have.

---

### Post by VastOne on 2009-11-20
I can't answer to your issues but I can ay that I have spent two weeks trying to get Samba and Win7 to work well together and have failed to the point of severe head banging wall treatments.... ](*,)](*,)](*,)

I can only maintain a persistent share from Win7 to my 64 bi Karmic server via IP browse and map a network drive that way.  I cannot get Karmic to get past the "Mount Failure- cannot retrieve share list from the server" when trying to connect to a share on the Win7 machine

I cannot say that it is totally a Win7 issue as I am having issues with another Karmic desktop (64 bit) failing o connect to the server via NFS, one which it connected to with no problems pre-Karmic.

I know this answers nothing to your issues, but since I am having parallel similar problems, I thought I would relay the info

---

### Post by pr0cs on 2009-11-20
I will likely try just vanilla XP tonite to see if I get the same issue or if it's just W7 causing the disconnects.  I can always work around and go from Unbuntu<-Windows so I'm not dead in the water but it will make my backups more difficult as all my dedicated backup software/hardware is on the Windows side and if the connection is not reliable that may be frustrating.

---

