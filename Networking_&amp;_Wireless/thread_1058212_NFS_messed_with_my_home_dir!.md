---
title: "NFS messed with my /home dir!"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2009-02-02
I am experimenting with NFS / roaming profiles.  I have a desktop that will be the server and a laptop that is the client.  I have two questions.  Firstly when I logged on to my laptop and mounted the home directory from my server onto my local filesystem the home folder got all screwed up.  My settings on both machine's for almost every single app was a mix of how I had them set on both machines.  My theme was 1/2 the desktop and 1/2 the laptop and evolution had lost my account!  Luckily I had a backup but why did mounting the home directory change settings?

my exports file on the server is

/home/ed     10.140.14.125(rw,no_root_squash,async,no_subtree_check)

My second question is that I am access my nfs via wifi so I have to login for the wifi to connect then the nfs mounts (because of fstab) and then I have to log out and log back in.  Why?

Thanks for any help!

---

### Post by lykwydchykyn on 2009-02-02
All your personal account-related settings are stored in your home directory.  If you mount a different home directory, it's going to change all that.  As to why it's half-and-half, it may be that stuff not installed on the desktop is retaining laptop settings (or default settings).

For the second question, you have to be connected to the network to mount the share.  If your wifi doesn't connect until you're logged in, then you can't mount the share to use as your home.

You mention "roaming profiles"; if you are referring to roaming profiles in windows, it works differently than this.  In Windows, you actually synchonize a local copy of your home directory to the server's copy (downloading files), and then upload the local copy back to the server on logout.  You could do the same on Linux with a pair of rsync scripts.

What you're doing is actually running the whole thing live off the server, without making a copy.  That naturally requires the server to be connected before you log in.

---

### Post by f37u5g0d on 2009-02-02
Thank you!  NFS is working now for me!  Now here I know is an ugly question.  What is considered "personal account-related" settings?  For example when I log in via the client machine compiz has different settings.  It would make sense that they are set by the user to the users liking which would make them user settings but they are also dependant on the hardware which obviously can change from system to system.  Are they user settings or not?

---

### Post by lykwydchykyn on 2009-02-02
Basically, if you don't have to enter your password to make the change, it's stored in your home directory.  I'm not sure of a better way to help you make the distinction.

---

