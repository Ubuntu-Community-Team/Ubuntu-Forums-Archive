---
title: "MythWeb password in Mythbuntu Control Center - how does it work and how secure?"
date: 2008-01-03
forum: Mythbuntu
---

### Post by asw20pilot on 2008-01-03
Hi all!

I have installed Mythbuntu and I am very pleased with it so far.

In the Mythbuntu Control Center in the Plugins section, there is an option to set a password for MythWeb. I am wondering how exactly this works? Does it create an Apache user and password for me? Or something else?

And how secure is it? I would like to open port 80 on my Mythbuntu backend to the internet so that I can access MythWeb from outside. But obviously I want the computer to be protected from unauthorized access.

Any information about the implementation of the password feature in Mythbuntu control center would be much appreciated!

Thanks,
Mikkel

---

### Post by murchball on 2008-01-03
I'm not exactly sure of the specifics, but I have read that if you open MythWeb to that internet thingy and you don't password protect it, random search engine bots can cause your recordings to be deleted.

---

### Post by asw20pilot on 2008-01-03
Hi murchball,

thanks for your reply. I realize that I need to password protect MythWeb somehow. What I am really wondering about is whether the password setting in Mythbuntu Control Center is secure enough or if I need to set up password security directly in Apache myself.

Best regards,
Mikkel

---

### Post by Nikas on 2008-01-03
> **asw20pilot said:**
> Hi murchball,

thanks for your reply. I realize that I need to password protect MythWeb somehow. What I am really wondering about is whether the password setting in Mythbuntu Control Center is secure enough or if I need to set up password security directly in Apache myself.

Best regards,
Mikkel

You dont need to do that yourself. The password is set in the files for Apache2. The password prompt that shows up has nothing to do with mythweb itself.
It's secure enough.

Hmm.. i hope you are with me on this one. Hard to explain in english. ;)

---

### Post by elj4176 on 2008-01-03
You can also change your apache2 port for a bit more security. Not much but a bit.

---

### Post by shad0w_walker on 2008-01-03
The password option in mythbuntu control centre is just a easy frontend to access the password function of apache. It uses the same method as you would to manually setup a password so its as secure as you would get.

But in the end, this all depends on how secure your username and password is.

---

### Post by asw20pilot on 2008-01-05
Thank you very much for all your replies! That was exactly what I needed to know. 
I am liking MythTV better every day. I just got a dual DVB-T tuner working. Recording has never been easier.

---

### Post by waynemcl on 2009-08-24
Thanks for the comments on how to get password for access installed. I did that, and it works. 

Now, I have changed my session login password, but the password for mythweb is still the old one. How do I update the mythweb password please?

Thanks, W.

---

### Post by asw20pilot on 2009-08-24
The MythWeb password (which is the Apache password) is separate from the password that you use to login to ubuntu. If you want to change the MythWeb password, you can do it in the same place where you set it in the beginning: the Mythbuntu Control Center.
See the screenshot at this page:
[http://www.mythbuntu.org/node/110](http://www.mythbuntu.org/node/110)

Mikkel

---

