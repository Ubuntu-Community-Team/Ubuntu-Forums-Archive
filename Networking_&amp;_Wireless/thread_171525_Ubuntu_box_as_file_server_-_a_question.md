---
title: "Ubuntu box as file server - a question"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by qpieus on 2006-05-06
I'm going to set up an Ubuntu machine as a file server. It will serve 3 other Windows machines in my house, to be used for file sharing and extra storage space. I know how to set it up to share a partition with my whole house, but I have a question that maybe someone can help me with. I've read tons of posts here and have not found an answer.

I believe the machine will be able to share the designated partition even if no one is logged on to the server machine (I'm going to set it up with "security=share" in smb.conf). 
Is this OK to do, or is there any security issue with doing that? 
I want to run this machine without a monitor, mouse and keyboard, so I'm envisioning just booting it up and letting it sit at the login screen. Does that sound OK, or just dumb :)

---

### Post by Iowan on 2006-05-06
> I want to run this machine without a monitor, mouse and keyboard, so I'm envisioning just booting it up and letting it sit at the login screen. Does that sound OK, or just dumb  IF the machine will boot up that way (some won't without modification), it works fine - a couple of my servers work that way.  SSH can provide whatever access is required.

---

