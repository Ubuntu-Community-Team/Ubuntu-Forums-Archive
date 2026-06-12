---
title: "VLC quitting unexpectedly in Ubuntu 14.04"
date: 2014-04-19
forum: Multimedia Software
---

### Post by jwjones1979 on 2014-04-19
I just upgraded from 13.10 to 14.04, and when I run VLC, my default video player, it will run for a few minutes and suddenly quit. I have never had this problem before and am unsure how to fix it. Any suggestions?

---

### Post by andrew.46 on 2014-04-19
Perhaps try resetting to default:

```

cvlc --reset-config

```

and this might be enough to tame your upgraded copy of vlc...

---

### Post by Cariboo1938 on 2014-04-21
> **andrew.46 said:**
> Perhaps try resetting to default:

```

cvlc --reset-config

```

and this might be enough to tame your upgraded copy of vlc...

Hello,
I  had the issue that vlc didn't start at all. My issue was SOLVED after running andrew.46's command!
Thanks man!

---

### Post by andrew.46 on 2014-04-21
Good to hear that your copy of vlc has come back to life :)

---

