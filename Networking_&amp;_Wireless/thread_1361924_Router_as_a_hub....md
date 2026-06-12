---
title: "Router as a hub..."
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by rmccutchan on 2009-12-22
HI-

I am really new to networking, but I am trying to take on a task for the education of it.  I have been looking for about a week, and can't find what I need, or maybe I am just don't understand.  I feel like if I accomplish this task, it would open the doors for more understanding and other projects (media servers, etc...)

The project:  I have 1 printer that I want to use on 3 computers via an Ubuntu server.  I have a Vonage (Motorola) router and using one of the computers as a server since the router does not have a place to hook up the printer.  Should be simple.

The hardware: 3 desktop computers - 1 with Windows Vista, and 2 with Ubuntu 9.10.
One of the computers is a dinosaur and will be used for the print server, and has Ubuntu installed with Samba.

I have a Linksys Modem feeding the Vonage router.  From the Vonage router, I attached a Linksys wireless modem strictly for my work laptop.

I installed SAMBA on the Ubuntu machine to be used as a router, and I was hoping it would be a simple as finding it under "Places".  But nothing seems to know that it is hooked up the the router.

Is this even a possibility to perform this with the hardware that I have?  Any information would be helpful.  Remember, I am still in the baby "steps" stage.  I can get to the command line and issue commands,  but I am not real familiar with it yet.

Thanks in advance.

Bob

---

### Post by ant2ne on 2009-12-22
You are kind of diving into a fairly complex (mixed environment) network without a whole lot of experience.

If the printer is set up on the host machine; There is an easier way. I'd use CUPS and connect to the printer from the windows machines and the linux machines using [http://servername:631](http://servername:631).

If you are gung-ho on using a samba based network, you might start with a simple file share on the linux server and verify that your network is up. (see my sig) And then add printing function.

---

