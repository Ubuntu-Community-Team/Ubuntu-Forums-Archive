---
title: "Mythtv only shows a box- Xubuntu desktop fine??"
date: 2010-04-02
forum: Mythbuntu
---

### Post by bb_145 on 2010-04-02
Hi,

For some reason I thought it would be a good idea to update my Frontend/backend from 8.10 to 9.04 using the built-in upgrade tool.  (Running on a thinkpad T40).  Now for some reason the frontend only shows a box (I've tried to attach a screenshot- hopefully it came through).  It appears to be working (I can still exit), but just the video is messed up.  The backend it still working as well- I can access it through mythweb, but when I try to access the backend configuration, the same thing happens.  If I exit the front end, I can see the XFCE desktop fine.  Anyone have some suggestions?  I have the Xubuntu desktop installed.

Thanks in advance

---

### Post by bb_145 on 2010-04-02
I should have mentioned that I'm using the open source drivers.

Thanks.

---

### Post by bb_145 on 2010-04-02
If it helps, here is the mythfronend log

```
Starting mythfrontend.real..
2010-04-02 23:15:15.040 New DB connection, total: 2
2010-04-02 23:15:15.040 Connected to database 'mythconverg' at host: localhost
2010-04-02 23:15:15.044 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2010-04-02 23:15:15.045 Enabled verbose msgs:  important general
2010-04-02 23:15:16.271 No theme dir: /home/greg/.mythtv/themes/G.A.N.T
2010-04-02 23:15:16.273 Primary screen 0.
2010-04-02 23:15:16.273 Using screen 0, 1024x768 at 0,0
2010-04-02 23:15:16.274 No theme dir: /home/greg/.mythtv/themes/G.A.N.T
2010-04-02 23:15:16.274 Switching to square mode (G.A.N.T)
2010-04-02 23:15:16.294 Using the Qt painter
2010-04-02 23:15:16.296 lirc init success using configuration file: /home/greg/.mythtv/lircrc
2010-04-02 23:15:16.297 JoystickMenuClient Error: Joystick disabled - Failed to read /home/greg/.mythtv/joystickmenurc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a0001f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a0001f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  66
  Minor opcode:  0
  Resource id:  0x3a0001c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a0001f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00032
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149(invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00032
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149(invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a0001a
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3a0000e
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x3a0001f
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  7
  Resource id:  0x3a00023
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  149
  Minor opcode:  4
  Resource id:  0x28
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00032
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  23
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00032
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  5
  Resource id:  0x3a00031
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
  Minor opcode:  6
  Resource id:  0x3a00031
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3a0001b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x3a00030
X Error: RenderBadPicture (invalid Picture parameter) 160
  Major opcode:  149
```

---

### Post by bb_145 on 2010-04-03
Never mind.  I updated again (this time to 9.10) and the problem went away.

---

