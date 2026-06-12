---
title: "errors in python-virtkey upgrade..."
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-09-27
```
Setting up python-virtkey (0.60.0-0ubuntu1) ...
file does not exist: /usr/lib/python2.6/dist-packages/python_virtkey-0.60.0.egg-info
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-virtkey (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python-virtkey (>= 0.60.0); however:
  Package python-virtkey is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 python-virtkey
 onboard
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Ehol on 2010-09-27
Same here.
I didn't find any bug related on Launchpad.
Should we file it in order to solve this problem ?

EDIT: Pardon me, there at least two : #648724 and #648749

---

### Post by tad1073 on 2010-09-27
same here...I just filed a bug about it but I can't find it now

---

### Post by uid313 on 2010-09-27
[https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648764](https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648764)
[https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648747](https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648747)

---

### Post by ljrmorgan on 2010-09-27
> **uid313 said:**
> [https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648764](https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648764)
[https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648747](https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648747)

Both of these are marked as duplicates of [this]("https://bugs.launchpad.net/ubuntu/+source/virtkey/+bug/648695").

Affect me too.

---

### Post by ergosteur on 2010-09-27
Add me to the list.
Was trying to add ubuntu-desktop to my Kubuntu 10.10 system.

---

### Post by whoop on 2010-09-27
So do we need to manually fix this or will the fix do this? The bug report says fix released but it's not showing up here yet.

---

### Post by philinux on 2010-09-27
> **whoop said:**
> So do we need to manually fix this or will the fix do this? The bug report says fix released but it's not showing up here yet.

Patience. You can just remove both packages if you want. The errors dont stop any updates to other apps.

---

### Post by whoop on 2010-09-27
> **philinux said:**
> Patience. You can just remove both packages if you want. The errors dont stop any updates to other apps.

Patience is not an issue here. I wouldn't even mind if it takes a year as I don't use the stuff..

I was just wondering if the fix would correct the dpkg errors if you all ready updated to this broken package...

---

### Post by M4570D0N on 2010-09-27
I can confirm this as well.

---

### Post by philinux on 2010-09-27
> **whoop said:**
> Patience is not an issue here. I wouldn't even mind if it takes a year as I don't use the stuff..

I was just wondering if the fix would correct the dpkg errors if you all ready updated to this broken package...

What I meant to say was that there's no need to do workarounds, a fix will turn up through updates I would guess.

According to the latest bug comment it's a packaging bug.

---

### Post by exploder on 2010-09-27
> What I meant to say was that there's no need to do workarounds, a fix will turn up through updates I would guess.

According to the latest bug comment it's a packaging bug.

I tend to agree with your comments. The Developer's are aware of the issue and the bug is not really hurting anything for the moment. I am sure an update will take care of the problem and it defeats the purpose of testing to work around things like this.

Edit: There was an update for "update manager", so the issue may already be resolved.

---

### Post by bmullan on 2010-09-27
> **exploder said:**
> I tend to agree with your comments. The Developer's are aware of the issue and the bug is not really hurting anything for the moment. I am sure an update will take care of the problem and it defeats the purpose of testing to work around things like this.

Someone stated that this bug doesn't hurt anything?   

Try to install UEC and see what happens.   

It fails to install everything on the CC because of a dozen or so dependency errors with "**python-virtkey**"

---

### Post by PaulW2U on 2010-09-27
The latest update, just downloaded, has put things back to normal.
Problem solved.

---

### Post by philinux on 2010-09-27
> **exploder said:**
> I tend to agree with your comments. The Developer's are aware of the issue and the bug is not really hurting anything for the moment. I am sure an update will take care of the problem and it defeats the purpose of testing to work around things like this.

Edit: There was an update for "update manager", so the issue may already be resolved.

+1 workarounds don't really help with testing.

---

### Post by thejon1337 on 2010-09-27
If anybody is still having this problem, a good

```
sudo aptitude purge python-virtkey
```fixed the problem for me, even if this isn't a real problem, it is annoying. Updating didn't fix it for me. I didn't bother reinstalling it, at least not yet.

---

### Post by jalampi360 on 2010-09-27
I installed the latest updates, which included some for update-manager, and it fixed the problem with "python-virtkey".

"All is well with the world now...." Whew!

---

### Post by seeker5528 on 2010-09-29
> **jalampi360 said:**
> I installed the latest updates, which included some for update-manager, and it fixed the problem with "python-virtkey".

None of that apt*, update-manager, etc... stuff fixed it for me, so, as one might expect, it was probably the updated python-virtkey package that fixed what was broken in the previously uploaded package. ;)

Later, Seeker

---

