---
title: "Installing rails broke remote access to subversion in eclipse"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by mayerk on 2010-02-26
Didn't really know where to ask this, but thought someone might have an answer.
 
I recently installed ruby on rails to my linux server using these instructions. [[COLOR=#660000]http://www.turnkeylinux.org/docs/rails/deployment[/COLOR]]("http://www.turnkeylinux.org/docs/rails/deployment")
The install worked and my test page worked, but since then I haven't been able to update or commit any of my code on subversion from my windows machine through eclispe. in fact, svn just hangs and i have to kill eclipse manually. 
At one point, i saw the message "no connection could be made because the target machine actively refused it"
It's almost like rails took over the port i was using for svn, so when svn tries connecting through the normal port it rejects the request. I've had svn working through eclipse for months and no changes/updates to windows or linux, except for rails, and i only did the steps listed in the document list above. I'm running Apache 2.2 on linux, but i checked all files in apache that rails might have been modified and didn't see anything related to svn.
Anyone heard of this, have an idea of what it could be?

---

