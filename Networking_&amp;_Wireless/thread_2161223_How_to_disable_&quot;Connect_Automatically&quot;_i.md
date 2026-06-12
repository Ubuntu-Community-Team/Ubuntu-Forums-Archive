---
title: "How to disable &quot;Connect Automatically&quot; in accidentally clicked wireless networks"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by mbman88 on 2013-07-09
I problem I've been having recently was causing me trouble when staying unconnected to wireless networks. NetworkManager will ALWAYS try to connect to wireless networks if you had clicked on them for whatever reason. If you click "Cancel" then it will proceed to the next network you clicked on for you to click cancel again. If you remain disconnected while "Wireless" is activated then within 5 minutes or less NetworkManager will try to connect to all the networks again. This is because "Connect Automatically" is enabled on all the networks you accidentally or non-accidentally clicked on but cannot access due to not having the password/permission. This is where I got stuck because I CAN'T disable "Connect Automatically" while I am not connected to the network. When I found the answer I decided that it caused me enough grief that I needed to share it with the community in case anyone else needed this information......

How to disable "Connection Automatically" on networks that require Security but you do not have the password (tested on Linux Mint 13 and should work for Ubuntu 12, also applies to all previous versions, it MAY or MAY NOT apply to later versions):

GUI: On the Search bar in your Menu type "Network" and it should bring up "Network Connections" as an option, click this. It will open the connection editor. Under the "Wireless" tab you need to choose the network you are having troubles with. Click "Edit" on the side pane. This is where you can choose to disable "Connect Automatically" however, you will ALSO need to go to the "Wireless Security" tab and choose "None" under the "Security" choice options. This will enable the beautiful "Save" button that you've been dying to click. You can hit "Save" now and you will no longer be auto connected to a network you can't access, thereby having to click "Cancel" and in my case I am using "Cinnamon" (Gnome 3 alternative) which means I have to click it twice due to some bugs that aren't worked out yet.

From the terminal I only know how to start "Network connections" in GUI:
type "nm-connection-editor" in terminal and it will open. Proceed to follow the directions as above. 

I hope this helps anyone else having the same problem.

---

