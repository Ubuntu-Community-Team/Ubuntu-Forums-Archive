---
title: "Mythbuntu 10.10 live -- I'm stumped"
date: 2010-12-02
forum: Mythbuntu
---

### Post by wh7qq on 2010-12-02
Been using various deb based linux distros for 7-8 years now and after some research, decided to make the jump into mythtv to build up a PVR.  I purchased an HDHomeRun box and downloaded the Mythbuntu 10.10 iso and burned it successfully.  I wanted to try the live disk to shake out my hardware but immediately started running into roadblocks:

At the "Install Welcome", I chose "Try Mythbuntu" which leads to a desktop with the tantalizing promise that "Home entertainment just got entertaining again."  Nothing else was forthcoming so I went into the "Applications" menu to Multimedia>Mythbuntu Live CD Frontend. It came back requesting a security key...(View in mythtv-setup on backend).  A button marked "Test Connection" returned "Could not find database login credentials"

Going to the cli and trying to run mythtv-setup was no help either, finding myself in a chicken-egg situation on groups.  Another tack got me into a similar mess on sql servers.

So my question:  Is there a way to run directly off this live disk or not?

Next question:  Is there a clear set of instructions somewhere that doesn't assume lots of things already set up or prior knowledge of mythtv?

Paul

---

### Post by thatguruguy on 2010-12-02
AFAIK, you can run the frontend off a livedisk, but not the backend.  Since you don't have a backend set up, you're getting less-than-favorable results.

---

### Post by thatguruguy on 2010-12-02
I realized I should have been more clear.  The backend does the heavy lifting of actually serving up content. It's the computer that you plug your tv cable into, and it streams and records live tv. It can also serve up videos, music files, etc., and maintains a database.

You can have multiple frontend computers all tied to one backend. I run both the backend and a frontend on the computer hooked up to my main television, and run the frontend on my kids' computer and on my own laptop.

You can run the frontend from a CD or USB, but without a backend set up somewhere it won't do you any good.

---

### Post by wh7qq on 2010-12-02
Thanks, thatguruguy.  It leads to the next question...how to install the backend?  I guess I need to clean up my partition table a bit and set up a dual boot for mythbuntu alongside my Mint?

---

### Post by thatguruguy on 2010-12-02
> **wh7qq said:**
> Thanks, thatguruguy.  It leads to the next question...how to install the backend?  I guess I need to clean up my partition table a bit and set up a dual boot for mythbuntu alongside my Mint?

Actually, you can install mythtv within your regular desktop environment.  I know it's packaged for ubuntu, so I assume it's packaged for Mint as well.  On ubuntu, at least, you can simply install the mythtv package from synaptic, and it will install both a frontend and a backend.  No reason to install a full OS.

---

