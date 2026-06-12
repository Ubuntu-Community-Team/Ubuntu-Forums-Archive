---
title: "Remote desktop to Win Shares"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by vcodek on 2011-12-17
Hy All.

Could someone explain to me, how could I
reach my shared folders on the remote Windows?

For instance, With Remmina I can connect to
the remote computer simply.

On Windows with mstsc on the local resources tab
we can enable local devices availability on the remote comp.
I am looking for something simmilar to my Ubuntu(ver. 11.10).

Thanks for Your help at all!

---

### Post by Jahid65 on 2011-12-17
you can use tsclient (very similar (lookwise) to MS RDP Client.

---

### Post by vcodek on 2011-12-19
Thanks!
But On 11.10 This is not available.

I found this:
rdesktop -f -r disk:MyShareName=/home/arpi/Sharedfolder -u Administrator 10.11.10.21 <-server IP

It worked for me.

Thanks for All

---

