---
title: "rsnapshot over encfs and sshfs"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by jvc26 on 2010-04-29
@admin: Apologies, seem unable to make a thread move, the old thread was [http://ubuntuforums.org/showthread.php?t=1465273](http://ubuntuforums.org/showthread.php?t=1465273)

Right, just a quick question about rsnapshot over sshfs and encfs.

I've set up an encfs filesystem, and when mounted on the remote machine remotely:

```
touch foo.bar
```
```
cp -al foo.bar foo.car
```

Works as one would expect it to.

The same is true on the local machine (The EncFS has External IV chaining disabled)

However, when the remote dir is sshfs mounted on my computer here, and then encfs'd to a decrypt mount on my computer, I can move files to it, and they go over the network and get encrypted, however:

```
cp -al <file> <file>
```

No longer works, I get 'not implemented' errors...

Any ideas? I thought since I dont have External IV chaining this shouldnt be an issue - I've tried without any of the file chaining options, again to no effect. All work remotely, or with both locally, but not over sshfs. Is this a quirk of sshfs?

Cheers,

J

---

### Post by jvc26 on 2010-05-02
Any ideas at all?

J

---

