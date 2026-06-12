---
title: "frontend problem"
date: 2008-11-02
forum: Mythbuntu
---

### Post by formol on 2008-11-02
hello, 

I'm trying to start the frontend on my laptop.  it said :

> 
formol@LinuxLaptop:~$ mythfrontend --service
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2008-11-02 17:50:58.790 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2008-11-02 17:50:58.791 MediaRenderer::HttpServer Create Error
2008-11-02 17:50:58.797 XScreenSaver support enabled
2008-11-02 17:50:58.797 DPMS is active.
2008-11-02 17:50:58.797 Empty LocalHostName.
2008-11-02 17:50:58.797 Using localhost value of LinuxLaptop
2008-11-02 17:50:58.802 New DB connection, total: 1

what is this?
thank you

---

### Post by formol on 2008-11-03
okay, I re-installed Ubuntu and the frontend.

when I start it in the menu, it do nothing.

in the system monitor, 

mythfrontend.real is "sk_wait_data", 

man page : 
sk_wait_data - wait for data to arrive at sk_receive_queue

what I should do with this?

thank you
----------------------------------------
edit : 

okay, I figure out the problem, but I don't know out to solve it

in the frontend configuration, as the IP of the backend, by default is "localhost".  so I changed it for the IP of my backend, but apparently it's not a solution, what should I write there?

thank you

---

### Post by Harry McCleave on 2009-04-01
Hi, I was having this same problem (im now stuck with no channels but thats another story) the solution for me was that I had added the MythTV port (6543) in the port field thinking thats what it wanted, entering 3306 (port for the mysql server) solved the problem for me. Hope this helps if someone runs into this in the future, if this is the problem someone should probably look at making the front end more clear what its looking for at that point in the setup.

---

### Post by formol on 2009-04-01
hi Harry

thank you for replying with a possible solution.  I will try to reinstall mythBuntu soon* and will try your solution.

*when school will be over...

---

