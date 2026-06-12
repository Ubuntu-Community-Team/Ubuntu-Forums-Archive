---
title: "Not able to access server files, please help"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by campbuds on 2008-12-13
I am using Hardy, and our server here at the office is MS server 2003 (or newer, I don't recall exactly)

Anywho, I can see the server, it is called fvserver, but when I go into it there is nothing coming up and I know that there are a ton of folders in it.

Also a user name and password is needed to access it and I am not being asked for one.

What do I do? I am starting to get people here interested in changing over but this would be a big road block and I need access to it also.

THANKS!

---

### Post by campbuds on 2008-12-13
moving to front until i get this resolved.

---

### Post by Iowan on 2008-12-14
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)This might be a good starting place...

---

### Post by campbuds on 2008-12-14
if this works it is still not a way that will work for our business on the whole.

I need a more simple solution. They need to be able to access the server files by clicking into the folders and just needing to remember their user and password.

Thanks though!

---

### Post by campbuds on 2008-12-20
Still looking for help with this.

---

### Post by LostMagix on 2008-12-20
Try to install 'samba via synaptic

---

### Post by campbuds on 2008-12-20
> **LostMagix said:**
> Try to install 'samba via synaptic

it already is, but thankyou

---

### Post by campbuds on 2008-12-22
still not solved

---

### Post by ocalot on 2008-12-22
I have seen this problem in other threads and there is currently no solution that I know of. There is a work around which is to use Konqueror which would allow access in the way you wanted.

---

### Post by campbuds on 2008-12-22
isn't that a web browser?

how about printing to the server printer? how would that be affected?

---

### Post by ocalot on 2008-12-22
> **campbuds said:**
> isn't that a web browser?

how about printing to the server printer? how would that be affected?

It is a web browser but when it opens it allows access to network files. For me I just start Konqueror I get a start page with a few options with one of the options being network folders. When network folders is clicked it pulls the option of choosing between samba shares and adding a network folder. Clicking on samba shares should pull up a list of your available networks. Once you picked the correct network its simply a matter of clicking on the correct server to log into it using your user name and password. As for server printers mine is working without any problems since I set it up so if your printer is having trouble I would suggest posting your printer settings so that I or someone else can look at them to see if there is anything we can do to get it working.

---

### Post by campbuds on 2008-12-23
I installed Konquerer, but when I click on the shortcut to navigate things like the network, a thing shows up on the panel saying "launching conquerer" but then nothing happens.

---

### Post by ocalot on 2008-12-23
I don´t have much experience with Konqueror since I only started to use it for the network file work around until everything is fixed with the normal way of accessing network files. The only suggestion that I could give you is to reinstall konqueror and see if it works.

---

### Post by campbuds on 2009-01-03
Konquerer works to access the files in Kubuntu.

But I still cannot access the server files in ubuntu

---

### Post by campbuds on 2009-01-27
ok, i can access all but the secure server filess. It said something about not being able to determine the security or something like that.

---

