---
title: "Telnet - How to send a single characters on it's keypress?"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by alex fisher on 2012-09-07
Hi - I have a telnet connection from my Ubuntu terminal to a device on my WiFi network. Having made the connection I want to continue by sending single key presses: e.g press letter 'a' and the letter 'a' is sent. Thanks in advance - Alex.

---

### Post by spjackson on 2012-09-07
I think you need to issue the
```

mode character

```command. You can do this after making the connection, or by putting it in ~/.telnetrc .

---

### Post by alex fisher on 2012-09-09
Thanks for the info spjackson. This method works in my arrangement with the 'mode character' command set in /.telnetrc. Unfortunately, if I disconnect/reconnect telnet reverts to it's previous mode. I can only recover 'mode character' by restarting my client terminal computer. Any ideas? Thanks - Alex.

---

### Post by d3v1150m471c on 2012-09-09
```

while true;do echo a; sleep 1; done | socat stdio, tcp-connect:$deviceip:$deviceport

```

---

### Post by spjackson on 2012-09-09
> **alex fisher said:**
> Thanks for the info spjackson. This method works in my arrangement with the 'mode character' command set in /.telnetrc. Unfortunately, if I disconnect/reconnect telnet reverts to it's previous mode. I can only recover 'mode character' by restarting my client terminal computer. Any ideas? Thanks - Alex.
According to "man telnet", the commands in ~/.telnetrc are meant to be executed after a connect. I don't know why that wouldn't be working. However, you should be able to type the escape character ^] and type "mode character".

---

