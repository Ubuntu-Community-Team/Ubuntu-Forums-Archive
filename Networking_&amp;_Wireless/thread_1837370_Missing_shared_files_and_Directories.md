---
title: "Missing shared files and Directories"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by Jonners59 on 2011-09-01
I have a PC that I use as a server to share files, pictures, videos, music, etc from.  It has a separate hard drive that these directories (folders) and files and media are stored on.

I have just noticed that some of the directories (folders) and files, pictures, videos etc are not visible to all machines: PC/Laptops on the LAN. This ONLY affects some machines and even more strangely the server itself.:(  Yet others see everything.:confused:

Looking at the properties of the files and folders there does not seem to be any differences.  How can this be and how do I fix it?

Any suggestions please?

---

### Post by lmarmisa on 2011-09-01
> **Jonners59 said:**
> I have a PC that I use as a server to share files, pictures, videos, music, etc from.  It has a separate hard drive that these directories (folders) and files and media are stored on.

I have just noticed that some of the directories (folders) and files, pictures, videos etc are not visible to all machines: PC/Laptops on the LAN. This ONLY affects some machines and even more strangely the server itself.:(  Yet others see everything.:confused:

Looking at the properties of the files and folders there does not seem to be any differences.  How can this be and how do I fix it?

Any suggestions please?

Are you using more than one samba user?. Have you enabled the guest access feature in some of the shared folders?.

---

### Post by Jonners59 on 2011-09-01
> **lmarmisa said:**
> Are you using more than one samba user?
Don't think so

> **lmarmisa said:**
> Have you enabled the guest access feature in some of the shared folders?.

I set up the share at the highest level folder and then ticked to replicate for all sub folders and files....

Is there a check/report that can be run?

I'll take a look tomorrow

---

### Post by lmarmisa on 2011-09-01
> **Jonners59 said:**
> Don't think so



I set up the share at the highest level folder and then ticked to replicate for all sub folders and files....

Is there a check/report that can be run?

I'll take a look tomorrow

You have to share only the highest level folder. All the files and folders included in that folder will be automatically shared.

What version of Ubuntu are you using?. Desktop or server?.

---

### Post by lmarmisa on 2011-09-01
If you wish to list the shares on your server, type this command:

```

smbclient -L serverhostname

```

---

### Post by Jonners59 on 2011-09-02
> **lmarmisa said:**
> You have to share only the highest level folder. All the files and folders included in that folder will be automatically shared.

What version of Ubuntu are you using?. Desktop or server?.

natty 11.04 desktop

The issue is that SOME machines can see all the files and directories but other, INCLUDING the PC (server) that the media is installed can not see ALL.  Most but not all.

---

### Post by lmarmisa on 2011-09-02
> **Jonners59 said:**
> natty 11.04 desktop

Did you use the graphical method for defining the shares?. I attach 3 captures. You can see the guest access option in the capture 2.

If you defined the guest access option in some of the shares but not in others some clients could see different files according to the samba username used (the user name of your account or the guest user). 

I do not recommend to use the guest access option for security reasons.

---

### Post by lmarmisa on 2011-09-02
> **Jonners59 said:**
> natty 11.04 desktop

The issue is that SOME machines can see all the files and directories but other, INCLUDING the PC (server) that the media is installed can not see ALL.  Most but not all.

Your issue is quite odd. Some additional information is required in order to diagnose your problem.

I would like to know if your server or other PCs can not see all the highest level share folders or if the problem is related to some files or folders located inside these highest level folders.

How many highest level folders have you defined?. How did you define these shared folders?. Did you use the graphical interface?.

Did you execute the command **smbclient -L serverhostname** on your server?. Check if the output of this command shows all the (highest) shared folders.

If you have other computers running Ubuntu, type that command there and check if you see any difference on the output.

---

### Post by Jonners59 on 2011-09-02
> **lmarmisa said:**
> Your issue is quite odd.
Your telling me!!!:confused:

> **lmarmisa said:**
> 
I would like to know if your server or other PCs can not see all the highest level share folders or if the problem is related to some files or folders located inside these highest level folders.

How many highest level folders have you defined?. How did you define these shared folders?. Did you use the graphical interface?.

It is SOME files and folders...  It's so bizzar.  Can see the upper most and sub folders and files, but not all.  I.e.  The stack is something like:
Documents (upper most folder) - Shared - Multi Media - My Pictures - Holidays...  then within this folder we have the holiday folders, so Easter 2007, Easter 2008, etc, but Easter 2011 is not showing on some, including the server the media is stored on.

Interesting all the folders missing seem from what I have noticed to be post Easter/April 2011, but I have not checked all folders, it is just noticeable in the holiday folder because of the labelling.

> **lmarmisa said:**
> 
If you have other computers running Ubuntu, type that command there and check if you see any difference on the output.

Looks the same....

---

### Post by lmarmisa on 2011-09-03
I suppose that you are not able to detect any pattern related to computers that see all files or those that do not see all files. For example, Windows has no problem showing all files and the problem is only limited to Ubuntu. I understand that the problem is deterministic (not random). I suppose that no odd characters are used in the names of the missing files/folders too.

If you have not modified by hand the file **/etc/samba/smb.conf**, the automatic configuration of samba is not easy to list. It uses several "binary" **tdb** files located at **/var/lib/samba**.

The command **sudo pdbedit -L** will list the users defined in samba:

```

luis@UB1104ENG:~$ sudo pdbedit -L
[sudo] password for luis: 
nobody:65534:nobody
luis:1000:Luis
luis@UB1104ENG:~$

```

The shared folders of Samba are defined in the directory **/var/lib/samba/usershares**.

Finally, I recommend this test. Define a new share with the folder **Holidays** and check if you detect the same problem when you access to Easter 2011 files after you have selected the  new upper most folder **Holidays**.

---

### Post by Jonners59 on 2011-09-05
> **lmarmisa said:**
> I suppose that you are not able to detect any pattern related to computers that see all files or those that do not see all files. For example, Windows has no problem showing all files and the problem is only limited to Ubuntu. I understand that the problem is deterministic (not random). I suppose that no odd characters are used in the names of the missing files/folders too.

No. all is standard.  Don't use Windows bar a W7 on a virtual machine on the server.  That too does not show the missing files/folders, and yes, deterministic.

> **lmarmisa said:**
> If you have not modified by hand the file **/etc/samba/smb.conf**, the automatic configuration of samba is not easy to list. It uses several "binary" **tdb** files located at **/var/lib/samba**.

I did some mods to smb.conf

> **lmarmisa said:**
> 
The command **sudo pdbedit -L** will list the users defined in samba:

```

luis@UB1104ENG:~$ sudo pdbedit -L
[sudo] password for luis: 
nobody:65534:nobody
luis:1000:Luis
luis@UB1104ENG:~$

```The shared folders of Samba are defined in the directory **/var/lib/samba/usershares**.


[HTML]server@server:~$ sudo pdbedit -L
[sudo] password for server: 
nobody:65534:nobody
root:0:root
server:1000:server,London,+44 (0)20 8xxx 1234,,
server@server:~$ [/HTML]Includes my telephone number - changed by me!

> **lmarmisa said:**
> 
Finally, I recommend this test. Define a new share with the folder **Holidays**  and check if you detect the same problem when you access to Easter 2011  files after you have selected the  new upper most folder **Holidays**.

Done, but makes no difference.  I GUESS because the machine I am changing it on is the server and the server can not see these files and folders itself.  I shall try on a machine that I know these were created by and can view them and see what happens.

---

### Post by Jonners59 on 2011-09-05
Update:
I had done some messing about and made it all worse, I think in so much as the files and folders are not visible on any machine.

That said, I took a peek in the Backup and the files and folders are all there, so I have just copied them back over to the original folder.  Don't ask why, I just thought it a good idea.  If it works then I'll do other folders.

However, IF it works, it does not answer the initial question or address the problem.  What caused it and how do I fix it.

UPDATE:
That worked.  By going to the back up location and directories I was simply able to copy over the backed up files and folders, they all appeared (I use the built in Lucky Backup app).

---

