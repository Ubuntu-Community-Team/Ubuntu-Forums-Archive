---
title: "Unable to open windows share from Ubuntu 12.04 network browser"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by Anifinity on 2012-05-27
Hello,

I am a new user to Ubuntu and I have just setup my HTPC with Ubuntu 12.04. I have 6 internal HDD's attached to a Windows 7 machine each with the entire drive shared and permissions set to read only for "Everyone". 

When I open Ubuntu's network browser I can see two copies for each of my shared drives. An example of this is my Windows drive 'I' which shows as "$I" and "I". When I try and open "I" it immediately gives an error "Failed to mount Windows share". If I try and open "$I" it advises "password required for share on $I arika-pc" which is the name of my Windows computer. My Windows computer has been setup with one user account named "Arika", is an administrator account and has no password.

Since this HTPC is attached to my TV I want to be able to double click a desktop shortcut and view its contents without having to enter a username, password, etc. This is very simple to do when networking multiple Windows machines but after several hours of searching and testing I am not able to get this to work on Ubuntu.

Can someone please advise me or direct me on how I can set this up?

Thanks.

---

### Post by Anifinity on 2012-05-28
I have managed to get this working if I create a Windows user with password. When Ubuntu prompts me for the windows share password I can enter the newly created user under the WORKGROUP domain with appropriate password and it successfully logs in.

Does anyone know how to get this working for Windows users that do not have a password?

Thanks.

---

### Post by kkraju4u on 2012-06-05
for me it works with the admin username and pass itself.
don't have to create a new one.
I think without pass its not possible.

---

