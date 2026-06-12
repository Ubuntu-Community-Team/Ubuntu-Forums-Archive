---
title: "Help getting lan-filesharing to work."
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by ZarathustraDK on 2006-07-09
Ok here's the deal, I'm trying to set up my smb.conf so it's possible to connect to my lan (there's both linux and windows-boxes on the lan), but somewhere along the way I screwed up big time with some of the settings, and I just can't seem to get it to work. Before I started screwing around I could acces other windows-machines' shared folders, but I couldn't share things myself, which I found quite annoying.

Anyway, can anybody cook up a small smb.conf that eradicates all those excess server-configuration lines that a mere mortal like me will never (ok, for the foreseeable future, at least) use? I'm not really sure what needs to go into [Global] and ["shared-folder-name"] in order for a folder to appear when browsing the network. I just need the ability to view other peoples shared folders and share some myself.

Any bids?

---

### Post by raldz on 2006-07-10
ok, first make sure you have the samba server and samba client installed.. if not, you could get it using synaptic.

so, you could view other machine's shares, which is not a problem, but you could not share your folders.. sharing the folders in Ubuntu could work by right click and share.. however, when other machines browse this share, it will ask for password, there, should add a samba user to access your folder.. open the terminal and execute this:

```
sudo smbpasswd -a <username>
```

Then supply a password.. or none if you like.. adding a username "guest" is good if you want it to work seamlessly with Windows machines..

---

