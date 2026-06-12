---
title: "Windows &amp; Linux server"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by KlearStatik on 2010-11-10
Me and my room mate would like to setup a server to hold large amounts of media. He uses Windows 7 and I prefer ubuntu. The server can be either but obviously I favor ubuntu.

My question is ....
 What steps do I need to take to setup an ubuntu server that will be recognizable to him?

Also would it be easier with windows?

---

### Post by Iowan on 2010-11-10
I haven't built a media server, but the [Server Guide]("https://help.ubuntu.com/10.10/serverguide/C/index.html") might shed some light...
Good luck! :)

---

### Post by davidshere on 2010-11-10
If it's going to be a server that simply stores media, you might just get a NAS.  [http://www.tigerdirect.com/applications/SearchTools/search.asp?keywords=nas+media+server\&searchbtn.x=27&searchbtn.y=13](http://www.tigerdirect.com/applications/SearchTools/search.asp?keywords=nas+media+server\&searchbtn.x=27&searchbtn.y=13)

If you really want to use an ubuntu server, you can use samba to share the data easily with a windows machine.

---

### Post by Whiteice on 2010-11-10
easy one. Im currently running a samba share system in my home and I use multiple systems to access it windows, linux, mac. All I did was setup a a storage drive in ubuntu named Media. Downloaded samba from the repository. Selected samba and I added the the media file to the listing of shared items and then selected existing users or created new ones. Then all I had to do was put them on the same workgroup in this case "workgroup" and then I would browse network drives on windows and my new shared drive is avail. all files just copy and past into the new drive. If you need further details on how to do this there are tons of tutorials online for it or just PM.

---

