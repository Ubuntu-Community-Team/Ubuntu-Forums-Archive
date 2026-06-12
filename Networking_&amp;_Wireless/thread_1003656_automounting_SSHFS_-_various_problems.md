---
title: "automounting SSHFS - various problems"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by bryonak on 2008-12-06
Hi folks,

up to now, I've been using simple scripts for mounting several shares via SSHFS. One drawback is the lack of automatic unmounting, so I'm looking for a way to smoothen this process.

AutoFS and AFuse come to mind... but let me say first that passwordless login is not an option. I don't want somebody who sits at my computer to be able to access files on my servers, and I'd like it to unmount after a few minutes.

First I've tried AFuse, which didn't work out because it kept asking me for a password no matter if I entered the correct one or not. This is probably what the AFuse [homepage]("http://afuse.sourceforge.net/") meant by "The only limitation is that the mount must not require any user interaction such as a password to be entered."
Anyone knows how to make it work **with** passwords?
Here's my command anyway:
```

afuse -o mount_template="sshfs [server ip] [actual local mountpoint]" -o unmount_template="fusermount -u -z %m" -o timeout="120" [local mountpoint]

```


AutoFS on the other hand allowed me to login with a password (despite lots of postings I've read claiming the opposite).
The main problem with the unmount (30 seconds is my current timout) is this: When I'm keeping a remote folder open in nautilus, it prompts me for a password every 30 seconds. The dialog should only pop up if I try to click on a folder/file after the timeout, not if I just wait with an opened remote folder.

Also I can't figure out how to have a folder mounted directly in another one, instead of requiring one more subfolder. For example my current shares are mounted as /media/autofs/share1, /media/autofs/share2, ...
I'd like this to be /media/share1, /media/share2, etc. If I try to specify the /media folder in auto.master, all other folders (cdrom) disappear, which is not what I want.


I've reduced my setup to only one share for testing... my auto.master:
```

/media/autofs /etc/auto.share1 uid=1000,gid=1000,--timeout=30,--ghost

```

and the auto.share1:
```

share1 -fstype=fuse,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#[server ip]\:/

```


Maybe the password prompt problem can be resolved by fine tuning the parameters, but I couldn't figure it out...

Thanks for your time!

---

### Post by bryonak on 2008-12-07
*bump*

Can anyone recommend an alternative? Nautilus bookmarks are said to hit performance badly, especially if you have a lot of them....

---

### Post by aurelieng on 2008-12-08
Key-based SSH authentication is considered more secure than password based logins, since you can disable the latter on your SSH server (and drastically reduce the consequence of any brute force attack against your server), and use a passphrase to protect your SSH keys and/or store them on a removable media such as a USB key.

No idea about the nautilus stuff. I am personally using konqueror to browse my automounted SSHFS shares, without any problem :)

Cheers,

Aurélien.

---

### Post by bryonak on 2008-12-08
Your point about security is true, but bruteforcing the passwords I use there takes a huge deal of time and horsepower... more than it's reasonable to assume I'll ever be the target of (by estimation over the thumb, a small botnet would need months to crack it). And if I ever get under a brute force attack, I'll be able to take countermeasures (like changing to key-auth ;)) long before they have passed a substantial amount of tries.
Additionally changing the default port gets rid of nearly all automated shots out there, so my current setup is *appropriately* secure in my opinion.

Still... my goal is that the remote folders are **not** reachable from my machine without local authentication. If someone's got an idea how to do this in Nautilus, either with password-based or key-based authentication (or something different), I'm all for it!


@Aurélien: Do you have any idea how Dolphin handles this? Maybe it's time to try out that splashy DE once again ;)

---

### Post by aurelieng on 2008-12-08
The problem with password-based authentication is that it is as weak (or as strong) as your password. Depending on your imagination, a simple dictionnary-based attack might be successful. This is why key-based authentication is more secure, by design.

In your case, a convenient way to cumulate the SSH key-based authentication and the password authentication would be to use a passphrase to protect your SSH keys. It would be more secure on the server-side (key-based only) and on the client side (not only your login password, but also the password protection of your keys, which is valid for a certain amount of time). See ssh-agent for more information about that.

Then, about Dolphin, I don't know. I wonder, in fact, why the password is asked when the timeout is reached using nautilus. As long as the directory is open (and my guess is that it should be the case with a file browser opened on this directory), it should not be umounted, and the password should not be prompted for... Perhaps it's time to switch to KDE ;)

Cheers,

Aurélien.

---

### Post by bryonak on 2008-12-09
While we both agree that key-auth has clear benefits, it's not the topic of this thread.

An example of what I'm doing currently (with bash scripts):
```
bin/mount.that.share
[enter password]
cp this /media/share/there
...
bin/umount.that.share
[enter password]

```

And the GUI equivalent thereof (I've even made launchers for the mount/unmount, though I hardly use them).


An example of what I want to do:
```
cp this /media/share/there
[enter password]
...
[auto unmount]
```

And the same with the file manager: just opening folders and having a simple password prompt if it happens to be remote.


So it's nothing dealbreaking, my current setup works fine... I just want to improve my workflow.

Can this be done with key-auth, without having to issue any additional command?
I have key-auth on my home desktop, where I mount various shares at boot (fstab), but I'm the only user on that machine.
As for my laptop and on another desktop other people (my friends, but nevertheless) have access to, I want a local authentication step.


About Nautilus... well it looks like a bug, since the countdown for the timeout should either not trigger at all or (if Nautilus really doesn't poll the remote folder) the password prompt should come up on the next user interaction.
I'm a bit reluctant to load up KDE just because of this, since I'd have to switch on at least two machines.

---

### Post by aurelieng on 2008-12-09
Well... if you use key-based authentication and protect your keys using a passphrase (managed with ssh-agent), I guess you can type the key passphrase once to temporarily unlock your SSH keys (local authentication step, based on a passphrase), then rely on them to authenticate to your server (remote authentication, based on a key). No idea on how to implement that in Gnome, though, because I'm using ttys or KDE :)

You could maybe have a look @ [http://en.wikipedia.org/wiki/Ssh-agent](http://en.wikipedia.org/wiki/Ssh-agent) ?

Aurel, not sure to be to the point

---

### Post by bryonak on 2008-12-09
Good idea, but it didn't work as intended...

First I've tried Seahorse, which is Gnome's default key agent. It lacks a timeout option on the password, so all the servers unlocked once in a session stay accessible, because the agent readily keeps providing the key.
Big security issue IMO, but on Launchpad it's merely a "wishlist" item.

SSH-agent on the other hand offers a timeout, but SSHFS can't read the cached keys of SSH-sagent (haven't checked Seahorse in this regard, but it's not useful to me anyway).

AFAIK the only key-auth SSHFS recognizes is those in the form of .ssh/id_dsa or .ssh/id_rsa (the "permanently authenticated" way), which is explicitly not what I want.


SSH-agent (having a password timeout) with Nautilus bookmarks could work, since it doesn't "mount" (using SFTP).
But I'm cautious about the bookmarks, since they aren't very highly spoken of... and I'd prefer SSHFS over (plain) SFTP.
This is why I'll probably just keep doing manual mounting/unmounting, hoping that Nautilus gets fixed.

For the sake of completeness, here are some guides I've used to this point (and lots of threads in these forums, but none were actually helpful):
[seamless sshfs-autofs]("http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/"), [autofs and sshfs]("http://www.tjansson.dk/?p=84"), [sshfs with autofs]("http://russoz.wordpress.com/2007/10/27/how-to-automount-sshfs-filesystems-with-autofs-on-linux/"), [automounting FUSE filesystems (afuse)]("http://www.linux.com/feature/128103")

I'm submitting a bug report on the Nautilus issue with autofs (password prompt), since this would be my preferred solution.

---

### Post by bryonak on 2009-05-19
It's become much worse with Jaunty :\

Now clicking on any (local or remote) folder anywhere (Desktop, home) makes Nautilus try to mount the remote SSHFS folder (gives me a password prompt). I haven't set any bookmarks.

If I open Thunar or browse my local file system in bash, everything's fine... that is, no remote folders get mounted.
When I browse the SSHFS test folder in Thunar or bash, they ask for a password once and then both keep the mount alive as long as I'm idling in a remote folder.
After leaving all remote folders the countdown set's in and unmounts... which is what Nautilus ideally should be doing as well, instead of having the countdown start as soon as I'm done opening a new remote folder. But this is a minor problem to the one mentioned above.

My current /etc/auto.master:
/media/SSHFS /etc/auto.sshfs --timeout=10,--ghost

My current /etc/auto.sshfs:
TEST -fstype=fuse,rw :sshfs\#USER@DOMAIN\:/

I've tried juggling around options like setting the uid/gid in auto.master or setting noatime,noemtpy and similar in auto.sshfs, without success.

---

### Post by bryonak on 2009-12-20
No luck with 9.10, Nautilus is still broken :\

---

