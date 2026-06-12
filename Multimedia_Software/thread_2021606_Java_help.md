---
title: "Java help"
date: 2012-07-09
forum: Multimedia Software
---

### Post by Skullxbagel on 2012-07-09
I wanted to download java so I could use various programs I wanted to download so I followed an online guide.[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

Now whenever I download and install anything, there are warnings and errors about oracle and java. Incase you didn't go to the website, here's the code I had typed in.
```

sudo apt-get purge openjdk*
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get updatesudo apt-get install oracle-java7-installer

```I didn't do the last few codes because errors started to occur. I was wondering if someone could help me get rid of these errors and help me install it correctly, Thanks.

---

