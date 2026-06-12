---
title: "Download speed up and down"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by henrymatt00005 on 2010-02-12
I am fairly new to ubuntu and have used mostly windows for my entire life. But I love ubuntu its awsome!!! The only problem I have is with downloading files from the internet. Specifically large files.

I have a 18Mg download speed internet connection and surfing the web is supper fast, streaming video is decent, etc. when I go to download a file 100 mg or so really anything my download speed will clime to about 1.3mg and then start dropping and level off at about 32 kb or lower.  if I pause and restart the download it will jump back up again for a while and then come back down. if i constantly pause and restart the file will download in roughly the same amount of time as if the connection was working properly. Any one have any advice on how to fix this?

---

### Post by kyletstrand on 2010-02-12
Do you still have a Windows partition?  If so, do you get the same problem in Windows?  Maybe try closing all programs running in the background to see if that will help the PC focus on the download rather than other unused programs.

Also try pinging the website from which you're downloading in the terminal.

```
@ubuntu:~$ ping www.ubuntu.com -c 50
```

This will ping the site 50 times, check the response times and see if it slows down throughout the pinging process.  You can change the last # to ping as many times as you want.

You could also check to see that your router/modem ports are open for downloading, whereas they can prevent good download speeds.

Don't know if any of that was any help, just thought I'd see if I can give any insight.

---

### Post by henrymatt00005 on 2010-02-12
Thank you very much for your advice I really appreciate it. after pinging ubuntu.com i didnt find any problems....
 
so how do you open ports for downloading? 
 
let me also add to the problem that I run a windows vm and within the windows vm it downloads seemlessly. it doesnt get cought up and slow down. 
 
the only time my connection is slow is when downloading files from firefox. I tried a number of different downloader programs last night but none of them improved my download time. I looked into the firefox slow download help forums and none of those helped either.
 
So my conclusion is that it has to be how ubuntu is talking with my router. I use a linksys wireless G router that I have my computer hard wired to and my second ubuntu machine conecting wirelessly to it. both computers have the same problem. 
 
Can you help me out by giving me an example of how my router should be configured to allow for fast downloading?

---

### Post by markbuntu on 2010-02-12
You could check that with speedtest.

You can also clear your cache occasionally by closing and restarting firefox.

---

### Post by ChrisBlizzard on 2010-02-17
I have the same problem I think.

Its not just Firefox though, its any download, including apt-get stuff and updates.

Starts off at 300 KB/s and drops off exponentially, as if the bandwidth is getting lost somewhere.

Anyone? Help? Please?

(desperation)

---

