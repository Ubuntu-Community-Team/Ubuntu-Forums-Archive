---
title: "ssh login does not work after DNS and ipnr change"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by Bioinfoswede on 2011-07-01
Hi!

I have had Ubuntu server (natty) running for some time now at work, but recently had to move the server to a server-room. When we did this the server also got a new ipnr and a new DNS name. Now when I login using the terminal and SSH from another computer, I am having problem with the terminal freezing.  I can login and list files using ls, change dirs using cd, and some other things, but when  try ls -l the terminal freezes. This also happens at times when I start a texeditor like nano or try to view a file using less.

What has happened? I log in using password. I can also not login using the DNS-name of the server, only by typing the ipnr. The DNSpeople can see nothing wrong at their end. I work at a university and the unix-support here is not so good, they mostly supply a place for me to place the server and then I have to administrate it myself.

Is some information stored by SSH on either the server on my client machine that needs to be removed?

Any help would be much appreciated, and please tell me if  should post this in another forum.

/Henrik

---

