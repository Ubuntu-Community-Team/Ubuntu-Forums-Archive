---
title: "Can I setup x11vnc NOT to send flash video or any video to the viewer?"
date: 2011-10-10
forum: Multimedia Software
---

### Post by alfonso78 on 2011-10-10
Hello,

I have the following configuration:

Ubuntu 10.10 Maverick Meerkat connected over WiFi and running x11vnc as such:

```
/usr/bin/x11vnc -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -o /var/x11vnc.log -forever -bg -rfbport 5900
```

This allows me to connect to the login screen remotely and share the same screen as Ubuntu from my client (VNC Viewer Free Edition 4.1.3 for Windows XP).

Everything is fine, but when I start playing videos in my browser over WiFi, the VNC viewer session gets really slow and unresponsive.

I wonder if there is a way to prevent x11vnc from sending any form of video over to the network to keep the viewer fast.

The reason why I start a video from VNC Viewer is because I use it as a sort of remote control. But once the video is playing I want to see it only on my big screen, not inside vnc.

Thank you for any suggestion!

If this is not possible (since VNC is sharing the same screen) how could I accomplish the same task?

---

### Post by krunge on 2011-10-10
What are the pixel width and height of the screen and of the video window?

---

### Post by alfonso78 on 2011-10-11
> **krunge said:**
> What are the pixel width and height of the screen and of the video window?

Thank you!

I'm not sure I understand how these info can help me, but anyway the video window changes all the time, since you tube puts the video in the main browser window but other websites pop up a new window for example.

Can you please explain me what is your idea?

---

