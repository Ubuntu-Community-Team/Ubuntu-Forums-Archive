---
title: "'net usershare' returned error 255: net usershare add: cannot convert name &quot;Everyone&quot;"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by bdr9 on 2010-12-03
Hi,

I am trying to create a SMB share in Ubuntu 10.04. I am right clicking on a folder, clicking 'Sharing Options', and then enabling the share. When I try to share the folder, I get the following message:

[B]Nautilus needs to add some permissions to your folder "test" in order to share it
The folder "test" needs the following extra permissions for sharing to work:
  - read permission by others
  - write permission by others
  - execute permission by others
Do you want Nautilus to add these permissions to the folder automatically?[/B]

I clicked 'add the permissions automatically'. Then, it goes back to the original box and it says:

[B]'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.
[/B]
It prevents me from creating the share. I have samba installed and I haven't changed anything that I can imagine causing this problem. Can anyone help me get this working?

Thanks,
bdr9

---

### Post by bdr9 on 2010-12-05
Sorry to bump this, but I really would like an answer. I need to share my drive with another computer on my network. Can anyone help me resolve this error?

---

### Post by P_Squiddy on 2010-12-26
Sorry, I don't have an answer yet, but I'm experiencing the same thing.  Just started happening (not sure when) and I've noticed it just this morning.  I'll try keep you posted if I find a solution!

---

### Post by Boondoklife on 2010-12-26
Search is your friend: [http://ubuntuforums.org/showthread.php?t=958457](http://ubuntuforums.org/showthread.php?t=958457)

---

