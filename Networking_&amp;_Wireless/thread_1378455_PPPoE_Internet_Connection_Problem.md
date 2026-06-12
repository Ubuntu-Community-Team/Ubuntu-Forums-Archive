---
title: "PPPoE Internet Connection Problem"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by syeef on 2010-01-11
I am a new Ubuntu 9.10 user. Now a days I have a serious problem to connecting my PPPoE internet due to Service Name. Before my ISP add a Service Name I could make a successful connection by apply the code ```
sudo pppoeconf
``` in the terminal.
But now the code sudo pppoeconf does not working.
By Googling I found a  solution; Apply the code ```
nm-connection-editor
``` in terminal. Then the Network Manager start then go to DSL tab then Add button. Then type my user name, service name and password. Then apply. My internet connected successfully.

[IMG]http://i453.photobucket.com/albums/qq254/syeef/Other/forum/pppoe.jpg[/IMG]

I can connect this by this way just for 2 days. Now it’s don’t connecting any more. I think if I apply this process in command mode it will fixed. Please help me. :cry:

---

