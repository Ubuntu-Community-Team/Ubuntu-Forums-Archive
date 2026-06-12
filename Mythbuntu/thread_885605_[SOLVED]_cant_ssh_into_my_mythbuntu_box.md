---
title: "[SOLVED] cant ssh into my mythbuntu box"
date: 2008-08-10
forum: Mythbuntu
---

### Post by styrofoam cup on 2008-08-10
This has had me baffled for hours.
I can ssh into all my other ubuntu boxes, but not my mythbuntu one. I'm running mythbuntu 8.04 and have installed the ssh server. then added the pub key to the .ssh/authorized_keys file. 

I was finally able to log in by using the local ip address on my lan. But if I try to use the public ip address I get the same error every time

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.

I'm running on a non standard port, and have forwarded the port in my router. if I try to login with the wrong port I get a not able to connect error - so its not that.

If I use the wrong username I get the same WARNING REMOTE HOST BLAH BLAH, so its kind of like I might be using the wrong username to login. I use

ssh -p2222 mediaboxname@publicipaddress

its the same username if I do the whoami command.
Like I said this has me baffled. Please offer any info or suggestions.

Thanks

---

### Post by tgm4883 on 2008-08-10
The problem is you're using the same address for multiple computers.  When your computer checks to see if the computer you are accessing is the same computer that it was last time, the check comes back false.  If it was an old computer you use to ssh into, you need to clear out the key that is tied to the older computer.  If you are trying to connect to multiple computers at the same IP, you may be able to set that up somehow, but IMO a better way would be to SSH into a single machine, then ssh to other machines from there.

---

### Post by nickrout on 2008-08-10
Read the full message and do as it says.

---

### Post by styrofoam cup on 2008-08-10
Thanks for the replies,
I was really tired last night. I think where I was getting stuck was how to add the correct info the the known_hosts file.
I did some googleing (always a good idea) and found the easiest way to add the correct info to the known_hosts file was to rename the existing file and then log in again and the new file will have the correct info.
 So thats what I did.
Both computers can log into the mythbuntu box now, laptop can log into my main server and everything seem fine.

cheers.

---

