---
title: "Vista permissions problems on Samba share"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by knottshawk on 2009-09-18
I created a Samba share on my Ubuntu 8.10 desktop... I can see and read its contents from my Vista desktop, but I cannot write. I verified that smb.conf lists that share as having full read/write permissions, but it isn't working. What should I be looking for?

Also, would my hard drive format matter in this case? (and how to check)

---

### Post by swerdna on 2009-09-18
> **knottshawk said:**
> I created a Samba share on my Ubuntu 8.10 desktop... I can see and read its contents from my Vista desktop, but I cannot write. I verified that smb.conf lists that share as having full read/write permissions, but it isn't working. What should I be looking for?

Also, would my hard drive format matter in this case? (and how to check)

To access a share you need the Linux permissions to allow access and the samba permissions to allow access (both). Check them both: post here the stanza for the share in smb.conf and also the linux permissions obatined by running this terminal command```
ls -l /path_to_shared_directory
```e.g. if the share is at /home/billy/share then run "ls -l /home/billy"

> Also, would my hard drive format matter in this case? (and how to check)Remote possibility, probably "no". What is the filesystem type (ntfs, ext3, etc). Check with this command:```
df -Th
```

---

### Post by knottshawk on 2009-09-18
ls -l /home/me/share
total 4
-rw-r--r-- 1 me me 11 2009-09-18 16:13 test

You can see I have a text file entitled 'test' in there right now.

df -Th results:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    147G  4.0G  136G   3% /
tmpfs        tmpfs    251M     0  251M   0% /lib/init/rw
varrun       tmpfs    251M  340K  250M   1% /var/run
varlock      tmpfs    251M     0  251M   0% /var/lock
udev         tmpfs    251M  2.8M  248M   2% /dev
tmpfs        tmpfs    251M  472K  250M   1% /dev/shm
lrm          tmpfs    251M  2.2M  249M   1% /lib/modules/2.6.27-14-generic/volatile

---

### Post by swerdna on 2009-09-18
I wanted to see the results from this: ```
ls -l /home/me/
```so I could look at the permissions on "share". Can you run that please? I think from looking at "test" that the Linux permissions are the problem, but need to confirm it.

Also very important to see the stanza in smb.conf for the share as I requested first up. You can see that if you run this command: ```
cat /etc/samba/smb.conf > /home/yourname/Desktop/config.txt
```the info will be placed in a file "config.txt" on your desktop. Be sure to use your user name instead of "yourname" in the command. The section I need is the paragraph [stanza] beginning with the share's name in [square brackets].

---

### Post by knottshawk on 2009-09-19
ls -l:
drwxr-xr-x 2 me me 4096 2009-09-18 16:13 share

cat /etc/samba/smb.conf > /home/yourname/Desktop/config.txt

(This I had confirmed earlier, which looks right/write to me) ;)

[share]
path = /home/me/share
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by Roasted on 2009-09-19
Are you logging in as yourself?

Like you have your user on your Linux machine, let's say Fred.

But you also have your user on Samba, is he also Fred?

You have 755 permissions on that directory, which means group + all others can't delete/write, which explains your issue. However, you should be the owner of that folder, and if you are the owner of that folder plus you're logging in as YOURSELF (who again, owns the share) you shouldn't have any issues...

---

### Post by knottshawk on 2009-09-19
That's weird... so I changed permissions and it works. Thanks!

Any tips on how to do the same with an external USB drive? Do I need to set it up in fstab to mount?

---

### Post by Roasted on 2009-09-19
I'm not talking permissions in terms of the Windows side, I'm talking permissions on the Samba side. For all we know, maybe you just hit "remember" when you logged in to your Samba share from Vista and that's why it bypasses it. 

With Samba, you have it set as writable. That's good. 

You also have 755 permissions on your Samba share, that's good ASSUMING the user you're logging in to the share as is the owner of that directory.

Who owns the share? Is it you?

Who logged in to the Samba share from Vista? Was it you?

I'm curious on your answers because 755 permissions means the owner has full control, however your problem seems to be having symptoms of "5" permissions (from the 755).

Did you create a Samba user when you first installed Samba? If you were doing it by terminal it would have been a command like "sudo smbpasswd -a fred".

---

### Post by knottshawk on 2009-09-19
> **Roasted said:**
> I'm not talking permissions in terms of the Windows side, I'm talking permissions on the Samba side. For all we know, maybe you just hit "remember" when you logged in to your Samba share from Vista and that's why it bypasses it. 

With Samba, you have it set as writable. That's good. 

You also have 755 permissions on your Samba share, that's good ASSUMING the user you're logging in to the share as is the owner of that directory.

Who owns the share? Is it you?

Who logged in to the Samba share from Vista? Was it you?

I'm curious on your answers because 755 permissions means the owner has full control, however your problem seems to be having symptoms of "5" permissions (from the 755).

Did you create a Samba user when you first installed Samba? If you were doing it by terminal it would have been a command like "sudo smbpasswd -a fred".

No, I didn't create a samba user. Yes, I'm the owner. You're losing me with the "logged in to the samba share" talk. Does "logging in" mean just connecting? 

As for my external usb drive issue, I've got it mounted, shared the mount over Samba, and am still getting permission issues when Vista tries to access it. I set permissions as 777, same issue.

me@me-desktop:~$ ls -l /mnt/external
total 0
-rwx------ 1 me root 0 2009-09-19 11:36 new file

---

### Post by Roasted on 2009-09-19
> **knottshawk said:**
> That's weird... so I changed permissions and it works. Thanks!

Any tips on how to do the same with an external USB drive? Do I need to set it up in fstab to mount?

What permissions are you running now? I'll clue you in on my situation and you can probably build off of it for your own, since every Samba file server situation can be completely different.

I have 4 users total that connect to my Samba share. Myself and 3 others. However I have shares for each user, all with different permissions.

I use a Samba GUI configuration tool known as "system-config-samba" (in synaptic). It's very simple but has enough features to do what I need.

All Samba users are part of the "sambashare" group. All Samba shares have 775 permissions, and are owned by jason:sambashare (I'm jason). That way all Samba user, in essence, have full control over each Samba share. The trick is, I allow/deny access to each samba share accordingly.

Example - Jason can get into anything, cause I'm the guy running the system so I can do whatever I want, right? Then there's my two brothers. Curt can get into Curt, but not Tyler's stuff. Tyler can get into Tyler, but not Curt's stuff, etc. This is done because SAMBA blocks it. Despite the fact my Ubuntu system has file/folder permissions allowing them to have full control, they can't do anything if they can't get in - right? 

So that's why I keep it simple. I own all folders. All Samba users are in 1 group I created. 775 permissions on everything. BUT I utilize the allow/deny access in the Samba GUI tool I spoke about above to create the security accordingly.

So, to be blunt, I wouldn't use 777 permissions on any Samba shares. 775 is a happy median cause it gives a lot of access to owner/group but limits all other users, which is a nice touch. However you need to customize everything to your situation accordingly.

About your edit - I've never had a need to put a USB drive in fstab. There have been a few times though that I'd plug in a USB drive and I wouldn't have access, cause it would be owned by root:root. Normally this happens when I have my USB drive plugged into a system running from a LiveCD, which I use a lot for troubleshooting. That's when I just pop in to terminal and run sudo chown me:me /media/XTernal (or whatever your drive is).

chown = change ownership (owner:group aka jason:sambashare)
chmod = change permission (777, 775, 755, etc)

---

### Post by Roasted on 2009-09-19
> **knottshawk said:**
> No, I didn't create a samba user. Yes, I'm the owner. You're losing me with the "logged in to the samba share" talk. Does "logging in" mean just connecting? 

As for my external usb drive issue, I've got it mounted, shared the mount over Samba, and am still getting permission issues when Vista tries to access it. I set permissions as 777, same issue.

me@me-desktop:~$ ls -l /mnt/external
total 0
-rwx------ 1 me root 0 2009-09-19 11:36 new file

I don't understand the "new file" part above. Is that the name of your drive?

I'm also confused how Samba works without having a Samba user registered. I mean if you have 777 permissions, I assume you'd be working off of the third 7 for permissions, meaning all users have access. But that's not really secure whatsoever...

I personally would do this. I'd create a samba user with a password. Then in smb.conf I'd add "valid users = you" under your share. Then perhaps setting ownership to you:you with 775 permissions would be a good idea. That's my personal take on it - you do what you see fit in accordance to what works the best.

Here's my section of my smb.conf:

[Jason]
        path = /home/jason
        writeable = yes
        valid users = jason

So when Curt logs in to my file server, he can access his folder. But when he tries to hit my folder, it prompts him to log in again - requiring Jason's credentials (which he doesn't know)  - not his own.

---

