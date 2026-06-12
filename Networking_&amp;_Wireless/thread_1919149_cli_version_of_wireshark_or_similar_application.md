---
title: "cli version of wireshark or similar application"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by jaz0nj4ckal on 2012-02-02
[COLOR=black][FONT=Verdana]Folks:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have searched high and low; however, I have not been able to find what I need. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My system hangs after 20 minutes of network packet captures with Wireshark, I need a way to do network packet captures from the CLI, and write to a simple txt file. I need all the information as Wireshark provides but only in a text mode so my machine will not crash. I am looking at generating over 12 hours of continuous data for a capture.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]In addition, (I am being greedy now), the ideal application will provide a method to break the files down into 10MB chunks and only log specific IP addresses.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]thanks.[/FONT][/COLOR]

---

### Post by jonobr on 2012-02-02
Hello


Im not sure of the second half of the question,

but for the first , there is [tcpdump]("http://danielmiessler.com/study/tcpdump/") which should already be on your system.

eg capturing a sip signalling trace

```
sudo tcpdump -vvv -i any port 5060
```


or ngrep which should be in the repos and theres a bunch of turotials out there

[heres a pdf ]("http://66.14.166.45/whitepapers/netforensics/sniff/ngrep%20Quick%20Tutorial.pdf") I did not look at it much though

---

