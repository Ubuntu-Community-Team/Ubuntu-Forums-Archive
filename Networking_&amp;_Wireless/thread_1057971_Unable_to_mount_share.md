---
title: "Unable to mount share"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Captain Rotundo on 2009-02-02
Recently I have been unable to access windows based shared on my network.  I have done this daily for the past several years until very recently.  Now when I click on a windows computer I get "Failed to retrieve share list from computer" for every computer. Has there been a recent update that caused this? How do I fix it?

I am running a fully up to do intrepid install.

---

### Post by Captain Rotundo on 2009-02-10
no help on this? still broken.

---

### Post by paulg1981 on 2009-02-11
Bump....exact same problem here although I can 'connect to server' with ip info correctly.  Just can't browse the network

---

### Post by dmizer on 2009-02-11
Please see the second link in my sig for how to mount a Windows share.

---

### Post by paulg1981 on 2009-02-11
> **dmizer said:**
> Please see the second link in my sig for how to mount a Windows share.

I appreciate the response but I can mount the share and navigate within it no problem.  My issue is when i try to browse the network instead of just mounting a share I get an error ' unable to retrieve share list from server '

Any ideas?

---

### Post by dmizer on 2009-02-11
Nautilus is terrible at handling Samba shares, so browsing is sketchy and always has been. There are a number of possible work arounds, but I have not found any to be satisfactory, which is why I wrote and still support that howto.

Things to check:
1) Disable firewalls (for testing)
2) Do not use firestarter (it doesn't handle netbios well)
3) Make sure that all computers on your network are a part of the same workgroup (this is critical and requires CLI edits)
4) Make sure you have winbind installed and nsswitch.conf correctly configured (this is also critical and also requires CLI edits)
5) Permissions on the share itself.

Other potential solutions include a correctly configured local DNS server for hostname resolution.

My experience has been that it's far easier, and gives consistently positive results when using a CLI tool like smbtree to find network resources and use mount.cifs to mount the share. Speeds are also better.

That said, I do recognize the need to have a browseable network share for casual users on the network.

---

### Post by Captain Rotundo on 2009-02-19
Well that link only made all networking not work, and the example nsswitch.conf file did not match mine. Mine has a bunch of other stuff on that line.  when adding wins to the end so that everything else works nautilus still can't retrieve list.

CLI mounting also doesnt work. I get:
mount error 112 = Host is down

The host is not down and is accessible from other windows machines and was accessible from Ubuntu prior to intrepid with NO changes to the windows host since then.

---

### Post by Captain Rotundo on 2009-02-19
I have now duplicated this error on a second machine with a fresh Intrepid install that has never done any windows sharing.

---

### Post by Captain Rotundo on 2009-02-19
when I try to CLI mount this appears in the log:

CIFS VFS: No response for cmd 114 mid 1
CIFS VFS: cifs_mount failed w/return code = -112

---

### Post by Captain Rotundo on 2009-02-19
One last update the program smbnetfs works perfectly with the windows machine that I have all the previous issues with

---

