---
title: "Samba disconnects randomly?"
date: 2011-01-18
forum: Mythbuntu
---

### Post by GnomicGhost on 2011-01-18
Hi all,
I recently put Mythbuntu 10.10 back onto my HTPC after having Ubuntu 10.10 on there with Myth installed over that.  I set up Samba shares on the original Ubuntu and didn't have a problem transferring my files from Windows 7 across wifi to it.
I had some other problems with that Ubuntu install so I went back to trying the actual Mythbuntu package.
I didn't get any of the problems I had with the Ubuntu install (several problems with the TV tuner) so I stayed with Mythbuntu and setup Samba and started sharing files again.

Now my problem seems to be that Samba *seems* to disconnect/drop off the network randomly. 
A few days ago I started by transferring my files overnight and woke up to Windows saying there was no Mythbox on the network anymore.  I tried again later that evening and I would get some files transferred over, then at a random time the Mythbox would drop off the network again.  It's happened randomly (but consistantly) over the last 2 days.

Now while it's off the samba share network, it is still connected to the internet and I have no trouble downloading or streaming from youtube.

This didn't happen at all when I was transferring to the Ubuntu box with Myth installed on that, it seems to be now that I've gone to using xfce desktop with Mythbuntu.

So, does samba have a setting anywhere that will 'shutdown' the network/share after a certain time? (though this does seem to be random times that I've noticed.)  I couldn't find that anywhere if it does.  And it never happened on the Ubuntu install either.
I haven't caught it in the act, but it doesn't seem to do it mid-way through a transfer of files, only seems to happen after they've completed the move.

I don't know if it is Samba or not, (still new using samba) so I'm not sure if there's any log files for it?  If so, where can one find them?
I don't quite understand why it will let me transfer files for maybe 30mins, 1hr, 2hrs or so, then drop off and disconnect.  Makes a long process even longer with the reboots haha :(
I'll post smb.conf (or anything else) if it's requested.

Thanks in advance! :)  Any help is appreciated very much.


Almost forgot, this is what shows up in windows, 'a', then if I mouse over that, I get 'b' appearing.
A: Windows can't find a computer or device name "MYTHBOX"    Detected

(mouseover)
B: "Windows can communicate with the name resolution server but can't find the host name."
I'm assuming that just means MYTHBOX is not shared/there anymore?

---

### Post by ian dobson on 2011-01-18
Hi,

Are you using a fixed IP address for your windows pc? 
When the connection dies can you still ping the mythtv box?
Do you see anything intersting in your system log file (dmesg)?

I've transfered alot of data to/from my server and have never seen any problems with samba. By alot I mean 5-7Gigabyte per day and on a really bad day 40Gb.

Regards
Ian Dobson

---

### Post by GnomicGhost on 2011-01-18
Ian, thanks for reply :)

Yep I always use static IP's on my home network so I know where each computer is.

I didn't even think about trying to ping it :o
But yep I can ping each way: Windows -> MYTHBOX, and MYTHBOX -> Windows, when it 'drops off' the network, with zero loss and 1ms.  Usual ping times.

Where would I find any log files that would be helpful with this?  I'm not that new to linux, but I am new to troubleshooting it and finding log files etc.

Thanks again for the help!

---

### Post by ian dobson on 2011-01-18
Hi,

One interesting log file can by displayed by typing dmesg from the command line. Samba creates it's log files in /var/log/samba not sure what format they are, but try looking at them with a text editor or cat <FILENAME> from the command line prompt.

Also do you see anything in the windows event log?

Regards
Ian Dobson

---

