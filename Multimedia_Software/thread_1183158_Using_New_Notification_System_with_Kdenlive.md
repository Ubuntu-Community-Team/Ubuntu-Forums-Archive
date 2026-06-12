---
title: "Using New Notification System with Kdenlive"
date: 2009-06-09
forum: Multimedia Software
---

### Post by ChaoticXSinZ on 2009-06-09
I wanted to get Kdenlive to use the new Jaunty Notification system instead of it's default ugly one.

Here's how I did it:

1. Launch Kdenlive.
2. Go to "Settings > Configure Notifications..."
3. Highlight "Rendering started".
4. Uncheck "Show a message in a popup".
5. Check "Run command"
6. Enter this in the space provided:

```
notify-send -i "kdenlive" "Kdenlive" "%s"
```

If you want it to come above other notifications use:

```
notify-send -i "kdenlive" -u critical "Kdenlive" "%s"
```

7. Highlight "Rendering finished"
8. Repeat steps 4 - 6.

Done.

Enjoy your new jaunty style notifications.

---

