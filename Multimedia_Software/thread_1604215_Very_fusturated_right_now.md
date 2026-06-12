---
title: "Very fusturated right now"
date: 2010-10-23
forum: Multimedia Software
---

### Post by mrwizard10 on 2010-10-23
Folks,

I need your assistance before I start reloading software.

I have a MP3 player which is owned by Root.  I have tried the following:
- in terminal - chown as both my usual log-in and root...operation not permitted  I ran chown as both su, root, and myself
- In Nautilus - I can't change any of the file attributes..again opening it as any of the users above.  

I used to be able to copy files over to the MP3 player but not the  Sandisk..but not I can't copy or do anything to the files on both.  

Any further help is greatly appreciated.

Thanks

Bob

---

### Post by eltonw on 2010-10-23
> **mrwizard10 said:**
> Folks,

I need your assistance before I start reloading software.

I have a MP3 player which is owned by Root.  I have tried the following:
- in terminal - chown as both my usual log-in and root...operation not permitted  I ran chown as both su, root, and myself
- In Nautilus - I can't change any of the file attributes..again opening it as any of the users above.  

I used to be able to copy files over to the MP3 player but not the  Sandisk..but not I can't copy or do anything to the files on both.  

Any further help is greatly appreciated.

Thanks

Bob

Your message header indicates that you're using the netbook remix .... in which case, you would be both root as well as the default and only user (unless you  created a separate user account). As such your user password would be what you'd use for any root administration functions.

Before you can get to the desktop you MUST enter the keyring password. I wonder if (somehow) you managed to get in, but forgot / failed to supply this important password? I note that with Maverick, even when I successfully enter this initial password, I get the dialog again requesting access to the keyring. 

[With Lucid, you were only required to enter the keyring once. I don't know if it is a bug or enhanced security, but Meerkat always makes me do two keyring responses]

... perhaps your problem has to do with the keyring? 

HTH...

---

