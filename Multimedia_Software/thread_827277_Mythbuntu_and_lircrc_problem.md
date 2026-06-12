---
title: "Mythbuntu and lircrc problem"
date: 2008-06-12
forum: Multimedia Software
---

### Post by slackey on 2008-06-12
I am trying to configure my remote to work with mthtv using the latest Mythbuntu. I used irrecord and got my lircd.conf file created. It seems to work correctly - when i run irw and press buttons on the remote all the right stuff appears on the console.

I then tried making my lircrc file using [http://lircconfig.commandir.com](http://lircconfig.commandir.com). When I try and run irxevent I get an error that says: ```
irxevent: bad file format, /home/user/.lircrc:3
```

Any thoughts on what the problem could be? I looked at the file and it seemed like everything was within the file format specified on the LIRC website.

---

### Post by slackey on 2008-06-13
Fixed my own problem. Turns out that that website gave me a file with DOS line breaks at the end of each line. I used dos2unix to fix the file and it works like a charm.

---

