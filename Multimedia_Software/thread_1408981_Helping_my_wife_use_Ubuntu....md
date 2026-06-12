---
title: "Helping my wife use Ubuntu..."
date: 2010-02-17
forum: Multimedia Software
---

### Post by Papa.Coen on 2010-02-17
Hi,

I've hooked my PC to my TV with the intention of using it for entertainment. Now I know how to login,start programs and all, but my wife... well, let's just say she doesn't.

Now I'd like to create an account for her, which...
- automatically and ONLY starts Songbird (or a mediacenter app.) 
- has only read rights on the music/media folder.
- can do nothing else but start Songbird (or...) and logout...
- ideally logout when closing Songbird (or...)

And all this in such a way that I can still enjoy a 'regular' Ubuntu experience.

Is this at all possible? I think I can figure out some of the rights, but what about auto starting an app and limiting app executing rights? And limiting services and all?

---

### Post by VertexPusher on 2010-02-17
You can configure a user account to run in kiosk mode by placing a script named ".xsession" into the user's home directory (/home/user/.xsession). If this script is present when the user logs in, it will be launched instead of the standard desktop session. The script may start any graphical application, preferably in fullscreen mode. When the user quits the application, he/she will be logged out as well. There will be no way to access filesystems except through ways provided by the application itself. There will be no desktop, no task bar, no system menu, not even a window border to resize the application.

Whether or not songbird is suitable for kiosk mode depends on whether it can be launched in fullscreen mode from the command line. But there are definitely some media center applications specifically designed for that purpose.

---

### Post by Papa.Coen on 2010-02-17
Thanks a bunch! I'll try and let you know how it worked (and if) out for me \\:D/

---

