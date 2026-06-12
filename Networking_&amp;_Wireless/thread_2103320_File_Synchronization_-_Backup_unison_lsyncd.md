---
title: "File Synchronization - Backup unison lsyncd"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by DOS286 on 2013-01-09
I need some help and advice. I have been beating my head on this problem for months and can't seem to find a solution.

Here's the situation. I have an ubuntu machine that is doubling as a sort of home server. I want the rest of the computers (ubuntu also) to synchronize each user's documents in real time with a folder on the server. The server then would backup a snapshot of the synced folders each night. I have a test setup working with unison and lsyncd running on the my laptop for the file synchronization. I'll use Back in Time on the server to take the nightly snapshots. My test setup mounts the server-side sync folder on my laptop and syncs with that.

Here's my issue. I don't want users to have access to other users files on the server. Ideally, they would not even have access to their own files on the server. The synchronization would run in the background and they would not have permission to mess things up.

I have looked into setting up unison and lsyncd to run over ssh, but I'm sadly ignorant in ssh. Is it possible to set this up to run when each user logs in and use credentials that they don't have access to? How would I go about that? I can't find any help files or tutorials for that kind of a setup.

My second choice would be to just mount a folder for each user, but I can't figure out how to do user specific mounting. fstab does not appear to offer this functionality.

The fact that I can't find any help on either of these methods makes me think that I'm going about this in completely the wrong way. Any other suggestions would be greatly appreciated.

---

### Post by ahallubuntu on 2013-01-09
I use rsync, and it works with ssh automatically.  You could simply create a separate user account on your Ubuntu server for each different user.  That way, it's easy to prevent them from seeing each other's folders - just use permissions that deny access. The user can see their own folders/files, though.

---

