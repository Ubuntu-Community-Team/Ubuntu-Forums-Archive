---
title: "Hauppauge remote not working on upgrade to Maverick Meerkat (10.10)"
date: 2010-10-10
forum: Mythbuntu
---

### Post by stafio on 2010-10-10
I upgraded my Mythbuntu install to Maverick Meerkat and now my Hauppauge remote is no longer working. Has anyone else run into this issue?

---

### Post by Name1ess on 2010-10-11
Hi, It's not much help but the same thing seems to have happen to me. I went for a clean install of 10.10 over a old installation of 9.04. Everything seems to be working OK apart from the remote which had worked before. I'm using a Hauppauge Nova-T 500 as my capture card.

---

### Post by stafio on 2010-10-11
I have [opened a bug]("https://bugs.launchpad.net/mythbuntu/+bug/658496") for this issue.

---

### Post by ian dobson on 2010-10-11
Hi,

I upgraded my frontend yesterday to 10.10 and after rebooting every keypress was echoed twice into MythTV (Up key caused the cursor to jump up two menu options).

I ended up having to edit the haupage remotes file, deleting all the remotes except the one I'm using (remote_350).

Using a homebrew serial adapter, and not a IR sensor attached to a tuner card.

Note: The lirc driver is now included in the kernel (in the staging area), and it could well be that you need to load a different driver for your ir sensor now.

Regards
Ian Dobson

---

### Post by purdueee on 2010-10-11
I'm having the same issue, repeated button presses using the remote_350 as well (actually a harmony configured as a 350).  irw shows 3 codes for each button push (1 + repeat as expected, and then a 3rd wich is the same as the first.  I'm also using a serial adapter.  Could you post the modifications you had to make to stop this behavior?

---

### Post by ian dobson on 2010-10-11
Hi,

Just edit the file /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge (or whatever remote file is included in yoir /etc/lirc/lircd.conf)  and remove all the "other" remotes, apart from the one you have.

Regards
Ian Dobson

---

### Post by rhpot1991 on 2010-10-12
Feel free to read about the issue here: [http://wilsonet.com/?page_id=95](http://wilsonet.com/?page_id=95)

---

