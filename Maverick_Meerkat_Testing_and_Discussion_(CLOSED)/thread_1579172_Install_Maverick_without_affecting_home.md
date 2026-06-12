---
title: "Install Maverick without affecting /home"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gauravbutola on 2010-09-21
So, I want to be prepared for the Maverick Meerkat :D clean installation without affecting my /home

I have a separate /home , could someone please explain me a complete 'how to' for a clean install without affecting /home.
I would want to do manual partition during installation.


I am really dying to try Maverick Meerkat. Whats your opinion should I jump onto installation on 10 Oct or should I wait for some early bugs to be fixed (as people say) a quick reply on this one.


Thanks
Gaurav Butola

---

### Post by gauravbutola on 2010-09-21
Bump

---

### Post by Mark Phelps on 2010-09-22
First, please STOP bumping.  It's rude and will not get you answers any sooner.

Second, the reason you're NOT getting answers is that you posted to the WRONG forum.  This forum is for released versions of Ubuntu.  Maverick is still in Beta, meaning, it's NOT released yet.

Please post your Beta questions to the proper forum -- Maverick Development.  Folks there should be able to help you with your Beta-related problems.

Good Luck

---

### Post by crichard on 2010-09-22
Wait for few weeks & install the full version is my recommendation unless if you want to experiment & help Ubuntu by testing & filling bugs, then, you are welcome to install beta version. Anyhow, let's come to the topic, to install Ubuntu without affecting /home partition, you've to go for manual portioning. 
While you reach the Prepare Disk Space, select **Specify Partitions manually(advanced)**, there you can see list of previously installed partitions. Pick the / partition (root) and click the Change button, Change the Type(File System) to ext4,put a check mark(tick) the format to clean your previously installed File System & pick the mount point as / . 
then, pick your /home partition & select Type to ext4 / ext3 (what it was earlier), **you should not check mark the format box** and pick the mount point as /home. 
Repeat the same for swap partition. I hope there's no selection for format.
Don't forget to keep the same user name(previous one) to login.
I'm used to following this method to install new version of Ubuntu rather than back up the whole system & install. I haven't tried 10.10 yet, there are some possibility of change in interface/ words but the idea is same. Read & understand it carefully while installing...

---

### Post by Iowan on 2010-09-22
Moved to Maverick Meerkat Testing and Discussion

---

### Post by CharlesA on 2010-09-22
Doing what crichard suggested would get it working. :)

---

### Post by VMC on 2010-09-23
> **CharlesA said:**
> Doing what crichard suggested would get it working. :)

Yes, I haven't tried what is wanting to do. Upgrade from previous release to Maverick keeping /home intact on same partition.

I do know that if I don't format previous Maverick partition and do clean install /home is left intact. I do that all the time.

Then again, it may work since it replaces all the special folders (/, /var, /etc, /bin, /lib, etc).

---

