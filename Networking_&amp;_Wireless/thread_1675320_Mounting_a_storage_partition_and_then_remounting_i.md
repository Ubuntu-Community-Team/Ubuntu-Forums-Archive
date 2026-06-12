---
title: "Mounting a storage partition and then remounting it"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Pawcatuck on 2011-01-25
We have three computers, linked very informally by a wired network.

The "main computer" has all my working documents on it. It currently has Ubuntu 10.04 LTS as the OS. If I'm in another room, I access those documents via Samba.

I was thinking that I would like to put all my working documents, music, etc. on a storage partition on the main computer. That way, I could install another distro side-by-side with Ubuntu, if for example I wanted to test-drive the new Xfce but leave my main distro alone.

I know how to mount the storage partition in **fstab**. But I am wondering if I could get into trouble.

Say I leave the main computer on, and go downstairs and start up one of the other computers, and decide to work on my novel :) . I've got my storage partition mounted in Ubuntu on the main computer, and from there I would mount it into another computer. My concern is that I think I'd be reading/writing twice in a row, from the downstairs computer to the mounted partition in Ubuntu, and from there -- I think almost immediately -- to that storage partition. And by that, I would be opening myself up to all sorts of errors and data loss.

And since that storage partition wouldn't have an operating system on it, I don't see how I could mount it directly from a remote computer.

So if I do what I plan, am I putting my working documents in danger by the extra rewrite? Or does this plan appear to be safe?

I hope this is clear.

Thanks.

---

