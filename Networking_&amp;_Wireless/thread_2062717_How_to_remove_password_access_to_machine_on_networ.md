---
title: "How to remove password access to machine on network"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by tim042849 on 2012-09-25
I have accessed machine1 on my network from an ubuntu 10.4 machine2.
It appears that I 'told' that machine2 to save the password for machine1. How 
can I remove the password for machine1 from machine2?
thanks
tim

---

### Post by CharlesA on 2012-09-25
It would help if you said how you were accessing the machine over the network.

---

### Post by Morbius1 on 2012-09-25
This is perhaps a prime example of the flaw in Unity. You have to know what you're looking for. 

Click on the Dash thingy > type passwords > then select Passwords and Keys

Then expand "passwords: login" and you should see an entry for the remote machine. Right click that entry and select: delete.

---

### Post by tim042849 on 2012-09-25
> **Morbius1 said:**
> This is perhaps a prime example of the flaw in Unity. You have to know what you're looking for. 

Click on the Dash thingy > type passwords > then select Passwords and Keys

Then expand "passwords: login" and you should see an entry for the remote machine. Right click that entry and select: delete.
Unity is not on this machine. I have gnome. If I go to Applications->Passwords and Encryption Keys,
I have three tabs : Passwords, My Personal Keys, Other Keys. I don't see anything there that
gives me a clue.
thanks, and I am confortable with the command line. Is there a file that controls this?

---

### Post by tim042849 on 2012-09-25
> **CharlesA said:**
> It would help if you said how you were accessing the machine over the network.
From Places->Networks, then clicking on the icon for the network machine.
thanks
tim

---

### Post by Morbius1 on 2012-09-25
> Then expand "passwords: login" and you should see an entry for the remote machine. Right click that entry and select: delete.
There is nothing there when you expand it?

---

### Post by tim042849 on 2012-09-25
> **Morbius1 said:**
> There is nothing there when you expand it?
A second window pops with one Tab Titled "Keyring".
It shows a folder Icon, with the following text
Name: login
Created: (nothing follow)
by right-clicking, I have an option to "Delete": Before proceding, please tell me, what
would be the result, If I were to choose that option.
thanks
tim

---

### Post by Morbius1 on 2012-09-25
Don't delete the main password. 

It should be obvious when you expanded it which one to delete if you really saved the password. Give me a minute to post a screenshot of what it should look like.

---

### Post by Morbius1 on 2012-09-25
If you really saved the password "forever" it should look like this:

---

### Post by tim042849 on 2012-09-25
> **Morbius1 said:**
> If you really saved the password "forever" it should look like this:
Understood. Nothing like it there. And the client machine retains the password somewhere,
because even when I reboot either the host machine (machine1) and the client machine (machine2),
machine2 still has access with no authentication.
thanks

---

### Post by Morbius1 on 2012-09-25
If machine2 were a Windows box I'd have an explanation for this but since it's not I'm at a loss to explain it.

If you were auto mounting this share by having an entry in fstab then that might explain it but I suspect you didn't do that.

Any chance the share on the server was changed to allow guest access?

---

### Post by CharlesA on 2012-09-25
> **Morbius1 said:**
> If machine2 were a Windows box I'd have an explanation for this but since it's not I'm at a loss to explain it.

If you were auto mounting this share by having an entry in fstab then that might explain it but I suspect you didn't do that.

Any chance the share on the server was changed to allow guest access?
Thinking the same.

Kinda wondering if changing that user's password on machine1 will prompt for a new password from machine2.

---

### Post by Morbius1 on 2012-09-25
> **CharlesA said:**
> Thinking the same.

Kinda wondering if changing that user's password on machine1 will prompt for a new password from machine2.
You would think that it would but you have to wonder what this "mystery process" is that's remembering the password. It might just happen all over again.

---

### Post by tim042849 on 2012-09-25
> **Morbius1 said:**
> If machine2 were a Windows box I'd have an explanation for this but since it's not I'm at a loss to explain it.

If you were auto mounting this share by having an entry in fstab then that might explain it but I suspect you didn't do that.

Any chance the share on the server was changed to allow guest access?
Yup!  I didn't mean to do it, but I did do it. (New OS to me, xubuntu 12.04).  
thanks for your time, I really appreciate it. All is good now.
tim

---

