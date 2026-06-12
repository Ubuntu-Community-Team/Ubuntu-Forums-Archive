---
title: "Issue with HTTP POST File Uploads"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by jonhall on 2010-09-23
We're having an issue with HTTP POST file uploads on our two Ubuntu PCs.  For some reason, whenever one of our users attempts to submit a file in an HTML form, the request times out, usually with a 500 Internal Server Error message.  This problem is not limited to one site, but occurs on all sites that use file uploads.  Also, the problem does not appear to be with our network, as a Windows 7 PC on the same network can upload files to the same sites without any difficulties.  The problem is not browser-specific; we have tested with Firefox, Epiphany, and Google Chrome and all produce the same results.  The issue is relatively new, and was first observed within the last month; before this time, both machines had no problems uploading files.

Does anyone have ANY idea what could be causing this?  I've tried a number of things, including rebooting the PCs, rebooting the network, disabling IPv6, etc.  I'm not very experienced in Linux system administration, but I can use the terminal and am familiar with some terminal-based diagnostic tools, so if you need any additional info or want me to try something, please let me know!  I've exhausted my own computer knowledge with regards to finding a solution to this problem.

---

### Post by jonhall on 2010-09-23
Does anyone have any suggestions concerning what could be causing this?  I really need to get this straightened out ASAP.
Thanks!

---

### Post by BkkBonanza on 2010-09-24
With little info to go on and making assumptions you're using Apache/PHP/MySql my somewhat experienced guess is that this is application specific.

More information about your web server and the application / language being used would help. Assuming you had it working, you could start debugging with a test script that handles the most simple POST request, and add code until it gets closer to the actual code you have accepting the POSTs.

Check if any recent (one month ago) upgrades have occurred. If you unknowingly upgraded PHP from 5.2 to 5.3 there are several areas where things will now fail, depending on the code. I had to revert and force non-upgrade on that to prevent app problems.

---

### Post by jonhall on 2010-09-24
Hello,
Thanks for your reply.  I'm afraid that you may have misunderstood my original post.  The Ubuntu systems are the clients, not the servers.  The problem is with uploading files to an external website.

---

