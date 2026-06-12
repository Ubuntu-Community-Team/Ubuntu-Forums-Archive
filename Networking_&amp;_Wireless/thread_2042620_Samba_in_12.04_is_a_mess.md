---
title: "Samba in 12.04 is a mess"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by quequotion on 2012-08-15
I have spent the last three days trying to figure out what is wrong with samba in Precise.

This is how the process should work:

1. Try to share a folder in nautilus.
2. Nautilus will ask permission to install samba and usershare dependencies.
3. Approve and install software
4. Folder is shared and available in the samba network.

This is what is happening.

1. Try to share a folder in nautilus.
2. Nautilus asks permission to install samba and useshare dependencies.
3. Approve and install software (occasionally this step fails due to an unrelated bug in apt, wherein *all* packages *suddenly* become "unsigned"; this step may also fail due to broken packages which try to overwrite each other or have broken install scripts)
4.** Everything falls apart. **Sometimes usershare makes an error about changing a username *i was never asked to supply* into some kind of code, which seems to have been a bug that was fixed ages ago (or maybe not). Sometimes everything looks fine, but the folder isn't shared or available on the samba network; in fact most of the time my computer doesn't appear in the network at all, let alone its shares.

Naturally, I assumed there'd be some hacky workaround as there most often is with any problem in linux and behold, there are hundreds of hacky workarounds to get samba working in Ubuntu.

None of them work. At least none of the dozen or so I've tried so far have worked, but I've limited myself to the ones that look plausible and make sense while avoiding the outlandish and overkill guides with no explanations.

I've pretty much given up on usershare. It doesn't look like there's any hope of getting samba to work that way anymore, but even a system configuration of samba fails every time.

The best I've gotten so far, is that after each attempt to hack samba into functioning, therefore with several different configurations, I get the same result:

1. A Windows computer on the network can see the Ubuntu computerin the network, and list its available printers and shares. 
2. As soon as I try to access a share, the Ubuntu computer immediately and permanently disconnects from the samba network.
3. Windows gives **two** errors in **one** dialog--That I may not have permission to access this share *AND* that the network name for the Ubuntu computer is no longer available.

There was a time when samba "just worked" in Ubuntu.


I almost forgot, apport actually detected some kind of bug in samba, but failed to file a bug report  because ***in 12.04 apport silently fails to file bug reports.***

---

### Post by quequotion on 2012-08-15
Well, 205th time's a charm I suppose.

I was trying[ this method]("http://ubuntuforums.org/showthread.php?t=1502265") *again*, with one extra step before getting started:

I purged all samba related packages except **libsmbclient**, **libwbclient0**, and **python-smbc**, *again*.

I kept just those three because they will take out important, dependent packages if removed.

Then I proceeded as recommended in that thread, *again*.

This time it actually worked.

This is still far from user-friendly and not at all how things are supposed to be done in Ubuntu.

The nautilus-share samba method needs work.
It really has to work in the LTS release at least.

---

### Post by Bucky Ball on 2012-08-15
Glad you managed to fix. Could you mark as solved to help others, please. ;)

---

### Post by quequotion on 2012-08-15
> **Bucky Ball said:**
> Glad you managed to fix. Could you mark as solved to help others, please. ;)

I'm not sure.

I'd like to mark it solved but, although I found a way to work around the problem, the problem isn't really solved at all.

Samba is still a mess, but it should work out of the box.

People shouldn't have to dig through the internet for hours or days or weeks to find a solution to problems that shouldn't exist.

Not everyone has the experience to understand what is broken when errors come out of places they shouldn't, talking about things they've never heard of.

Perhaps it's unavoidable now and then, but "Share this folder..." should really just work as it really just used to and does in other distributions and even Mac OS and Windows.

For the sake of the forum's guidelines, I suppose I should mark this thread solved, but I'd rather mark it something more accurate, like [WORKAROUND].

Solved is not at all how I feel about the issue.

---

### Post by Bucky Ball on 2012-08-15
Got ya. ;)

---

