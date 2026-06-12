---
title: "Mass Name server lookup"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by Davisimo on 2012-03-05
Is it possible to use the name server lookup tool thats built in with Ubuntu to search multiple domains?

I have a list of 1000+ domains and need to find out the name servers of each domain, i have tried using terminal but my output file keeps on getting separated into multiple file after a unspecific try's?

The command i tried was 

host -t NS domain.com> Name Server.txt
host -t NS domain.com >> Name Server.txt
host -t NS domain.com >> Name Server.txt
host -t NS domain.com >> Name Server.txt

Any help would be appriciated

Tom

---

### Post by TheFu on 2012-03-05
This can be solved using a pretty simple bash script. It appears you aren't quoting the filenames (that could be just a posting error) which have spaces in them and that you are asking the same question every time.

host -t NS domain.com >> "Name Server.txt"
host -t NS domain2.com >> "Name Server.txt"
host -t NS domain3.com >> "Name Server.txt"
host -t NS domain4.com >> "Name Server.txt"

I'd use a loop and read the domains from another file. 
You can learn to do this yourself: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

