---
title: "XDMCP fatal error"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by duxbuz on 2011-07-20
Hello. I previously had my xdm server running and it allowed me to use cygwin to run remote desktop with X -query x.x.x.x :1

But recently i noticed it had stopped working.

I get an error as shown in image, and i noticed that it mentions a 169.x.x.x. address.

I am wondering if anyone had had this problem. not sure where its getting this 169 address from. I do know there are some vmnet interfaces when i run ifconfig, although none are 169.x.x.x addresses.

I do not remember when this error started occuring.

xdm service seems to be running and config files seem ok.

Anyone help?

Wonder if its related to these virtual nics?

Thanks. 



[IMG]http://i1025.photobucket.com/albums/y319/duxbuz/xdmcp.png[/IMG]

---

### Post by duxbuz on 2011-08-04
Solved!

I had to add the -from otion to the X -query



So it looked like this:



x -query <server ipaddress> :1 -from <myipaddress>




Also it seems that I needed an entry for the client I am connecting from in the hosts file on the xwindows server.



I didn't expect to need that as dns server has host records for all machines on network.



Anyway it works now :)

---

