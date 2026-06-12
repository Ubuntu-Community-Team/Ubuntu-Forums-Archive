---
title: "Installing spotify ubuntu 11.04 and up!"
date: 2012-10-18
forum: Multimedia Software
---

### Post by valroadie on 2012-10-18
I thought I would make a thread addressing how to install Spotify the music client. 
I have done this on ubuntu 11.04 and up so I am not totally sure on ALL distributions.
First you need to open a terminal: ctrl+alt+t
Then you need to add the public spotify key to your list:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
```

Next you need to add the repository:
```
sudo gedit /etc/apt/sources.list.d/spotify.list
```

When the text file opens, copy/paste this line into the text file and save it. 
```
deb http://repository.spotify.com stable non-free
```

Almost done! The final step:
```
sudo apt-get update && sudo apt-get install spotify-client-qt
```

And that's it! You have just installed spotify! 
No need to reboot/re-log it's ready to go. :) 
ENJOY!

---

