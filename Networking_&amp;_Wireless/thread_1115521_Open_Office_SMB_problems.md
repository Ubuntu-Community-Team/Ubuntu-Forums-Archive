---
title: "Open Office SMB problems"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by longtom on 2009-03-30
I real showstopper for me in Open Office is, that one can't open files on a Windows network (and on any other network for that matter).
I can open those files with gnome and any other non Open Office file.  There are some workarrounds in cyberspace, which than produce their own hangups and need another workarround etc...

Now, this is something which I would, in a Version 3.0 and not 0.3, expect to be working and considered as "basic".  I am not working on some or other obscure OS but Ubuntu....hmmm

Am I ungrateful and must I go back to MS Office?

---

### Post by lancest on 2009-03-30
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=1056900"). They were able to make it work.

---

### Post by longtom on 2009-03-30
> **lancest said:**
> Take a look at [this]("http://ubuntuforums.org/showthread.php?t=1056900"). They were able to make it work.

Thank you very much.

However, this is either extremely complicated (for me as beginner anyway), or it needs a revamp of the network with fixed IP addresses.  Not really feesable right now.

I could also see, that the OP didn't find a lasting solution in the end and the thread is abandoned.

I made my peace with that.  In Open Office you cannot open files over a network in Ubuntu.  This is a major weakness no other program, I use, appears to have.  So I use Gnumeric for my spreadsheet files - luckily I don't use and/or edit to many write files over the network....
I also read myself through some threads in the Oo forum - others have the same problem, even in Windows it appears.  There doesn't appear a permanent cure available.

I will not recreate the whole network with 20+ machines to suite the weakness of Oo and than I am not really sure, if it will make a difference.  Doesn't sound right to me....

It also appears, that this bug has been filed a couple of times - without any success.  Remarkable...

---

### Post by dmizer on 2009-04-03
> **longtom said:**
> I will not recreate the whole network with 20+ machines to suite the weakness of Oo and than I am not really sure, if it will make a difference.  Doesn't sound right to me....

It also appears, that this bug has been filed a couple of times - without any success.  Remarkable...

Actually, what you are calling a failure of Open office is not a failure of Open Office. It's a problem with how Nautilus handles Samba. This is why the bug has been filed several times and been rejected.

Open office does in fact cooperate perfectly well over samba as long as you don't use the places > connect to server option. If you mount with /etc/fstab, there is no problem at all as long as you use the "nobrl" option in the mount command.

I suspect that you would _not_ encounter this issue if you used Kubuntu instead. KDE seems to (or has in the past) handle Windows shares much better than Gnome's Nautilus.

I do sympathize with you that /etc/fstab is extremely complex for users to correctly configure, and I also understand your reluctance to tackle the seemingly monumental chore. However, if you DO decide to try it, I'd be more than happy to walk you through the process step by step.

If not, that's your choice but blame Nautilus for the problem, not Open Office. :)

---

### Post by longtom on 2009-04-03
> **dmizer said:**
> Actually, what you are calling a failure of Open office is not a failure of Open Office. It's a problem with how Nautilus handles Samba. This is why the bug has been filed several times and been rejected.

Open office does in fact cooperate perfectly well over samba as long as you don't use the places > connect to server option. If you mount with /etc/fstab, there is no problem at all as long as you use the "nobrl" option in the mount command.

I suspect that you would _not_ encounter this issue if you used Kubuntu instead. KDE seems to (or has in the past) handle Windows shares much better than Gnome's Nautilus.

I do sympathize with you that /etc/fstab is extremely complex for users to correctly configure, and I also understand your reluctance to tackle the seemingly monumental chore. However, if you DO decide to try it, I'd be more than happy to walk you through the process step by step.

If not, that's your choice but blame Nautilus for the problem, not Open Office. :)

Thank you very much for your explanation.  I hear you that not Oo is to blame but Gnome/Nautilus.

Gnome/Nautilus doesn't seem to have similar problems with Gnumeric, Abiword or, in fact, any other application I used this far.

What is it, that makes Oo and Nautilus being so unharmonic?

Any way I could switch to Kubuntu without having to start my whole setup from the very beginning?

Oh yes - and thank you for the offer to walk me through my problem - I appreciate that and might still take you up on it.

---

### Post by hyper_ch on 2009-04-03
if dmizer is right then just add the smb drive to your fstab or write a little script that mounts it into your local file system upon execution. That way you don't have to use nautilus.

---

### Post by longtom on 2009-04-03
> **hyper_ch said:**
> if dmizer is right then just add the smb drive to your fstab or write a little script that mounts it into your local file system upon execution. That way you don't have to use nautilus.

Would that look like this in fstab?

```

//annelize/order%20book /media/order_book  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

```

were order book would be the directory where the Office file is located.  I did that, directory mounts, but file still doesn't open with Oo.  Where is my mistake?

---

### Post by dmizer on 2009-04-03
Perhaps we can get this solved quickly?

A couple of things. First of all, you've escaped your space incorrectly. you need to use \040 to escape spaces in fstab. Second you're using a smb option for cifs (codepage=unicode,unicode). That option is unnecessary.

Try this:
```
//annelize/order\040book /media/order_book  cifs  guest,rw,iocharset=utf8,nobrl,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by longtom on 2009-04-03
> **dmizer said:**
> Perhaps we can get this solved quickly?

A couple of things. First of all, you've escaped your space incorrectly. you need to use \040 to escape spaces in fstab. Second you're using a smb option for cifs (codepage=unicode,unicode). That option is unnecessary.

Try this:
```
//annelize/order\040book /media/order_book  cifs  guest,rw,iocharset=utf8,nobrl,file_mode=0777,dir_mode=0777 0 0
```

Thank you - this worked very good.  
Do I need to do this with all directories I want to use on the network?
Is there a way to mount in such a way that the mount doesn't show on the desktop?  THis might get cluttered after a while....;)

> 
Isn't this getting off topic? 


It is...  but by now I'm feeling I am so close that I would ask just a little bit of patience with me, please.  It's still about my Open Office Experince - in a way....:p

---

### Post by dmizer on 2009-04-03
Glad that worked so well for you! Had a few minutes on the train, so I though I'd stop in and see if that worked for you or not.

Yup, you'll need to do that for each directory on the network. If you don't want them to show up on the desktop, you can make the mount point in your home directory. For example:

mkdir /home/you/network/order_book
mkdir /home/you/network/directory2
mkdir /home/you/network/directory3
mkdir /home/you/network/directory4
etc ...

Then your mount command would look like this:
```
//annelize/order\040book /home/you/network/order_book  cifs  guest,rw,iocharset=utf8,nobrl,file_mode=0777,dir_mode=0777 0 0
```

ps. I split these posts out into a support thread because they were off topic ;)

---

### Post by longtom on 2009-04-04
> **dmizer said:**
> Glad that worked so well for you! Had a few minutes on the train, so I though I'd stop in and see if that worked for you or not.

Yup, you'll need to do that for each directory on the network. If you don't want them to show up on the desktop, you can make the mount point in your home directory. For example:

mkdir /home/you/network/order_book
mkdir /home/you/network/directory2
mkdir /home/you/network/directory3
mkdir /home/you/network/directory4
etc ...

Then your mount command would look like this:
```
//annelize/order\040book /home/you/network/order_book  cifs  guest,rw,iocharset=utf8,nobrl,file_mode=0777,dir_mode=0777 0 0
```

ps. I split these posts out into a support thread because they were off topic ;)

And that - works like a charm.

Thank you very much - another Ubuntu battle fought and won - with a little help from my friends!:-D

PS:  Hope you have a wonderful weekend with all the flowers in full bloom.  One day I'll join you for that - one day...

---

### Post by longtom on 2009-04-04
Ah - now, after a restart, the share does pop up on the desktop....that's a bit of a drawback.

Things do get cluttered now.  Is there a way I can avoid this?

---

### Post by dmizer on 2009-04-05
Well, I'm back in the office now and I haven't had a chance to look at this yet. I am surprised that this is happening actually. What version of Ubuntu are you using?

---

### Post by longtom on 2009-04-06
> **dmizer said:**
> Well, I'm back in the office now and I haven't had a chance to look at this yet. I am surprised that this is happening actually. What version of Ubuntu are you using?

Intrepid 8.10 - as it says there left in the panel right underneath my passport photo...;)  (I know, I should use some teeth whitener....)

---

### Post by dmizer on 2009-04-06
Actually, I'm not in the habit of looking there. It was only recently that the feature was enabled. Thanks for reminding me.

Figured out how to get those directories from appearing on your desktop.

Open a terminal and type:
```
gconf-editor
```

Then go to:
apps > nautilus > desktop

Uncheck "volumes_visible" :)

---

### Post by longtom on 2009-04-06
> **dmizer said:**
> Actually, I'm not in the habit of looking there. It was only recently that the feature was enabled. Thanks for reminding me.

Figured out how to get those directories from appearing on your desktop.

Open a terminal and type:
```
gconf-editor
```

Then go to:
apps > nautilus > desktop

Uncheck "volumes_visible" :)

Now - that is quite nifty - thank you.

The problem is (I keep running into those..), that I do have permanent shares I would like to see on my desktop...

Is there a way I can make a permanent launcher for those?  I tried /media/<directory> - but that didn't do it.

---

### Post by dmizer on 2009-04-06
You can make a symbolic link from the moutpoint to your desktop

```
ln -s /media/<directory> /home/you/Desktop
```

---

### Post by natxoo on 2010-02-26
I've solved it installing gvfs-fuse package. This make openoffice use fuse, and an automagically 'copy' in /home/user/.gvfs

---

