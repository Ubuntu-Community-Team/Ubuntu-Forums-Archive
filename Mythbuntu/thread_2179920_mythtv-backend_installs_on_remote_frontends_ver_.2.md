---
title: "mythtv-backend installs on remote frontends ver .27"
date: 2013-10-10
forum: Mythbuntu
---

### Post by williammanda on 2013-10-10
All of my remote frontends have mythtv-backend installed. I installed mythtv-frontend via synaptic and there wasn't any backend installed at that time. The only way I can think that it  got installed is through updating. Is mythtv-backend now a standard install on remote frontends? If so...please explain. 
Thanks

Using Ubuntu gnome 13.10 with Mythtv 0.27 with updates 2013-10-10

---

### Post by tgm4883 on 2013-10-10
> **williammanda said:**
> All of my remote frontends have mythtv-backend installed. I installed mythtv-frontend via synaptic and there wasn't any backend installed at that time. The only way I can think that it  got installed is through updating. Is mythtv-backend now a standard install on remote frontends? If so...please explain. 
Thanks

Using Ubuntu gnome 13.10 with Mythtv 0.27 with updates 2013-10-10

No it is not something that we would require. You can check /var/log/apt and see when and why it was installed.

---

### Post by williammanda on 2013-10-11
This is the output from the var/log/apt:

```
Start-Date: 2013-10-10  13:46:19
Commandline: /usr/sbin/synaptic
Purge: mythtv-backend:amd64 (0.27.0+fixes.20131006.77db957-0ubuntu0mythbuntu4)
End-Date: 2013-10-10  13:46:26

Start-Date: 2013-10-10  13:56:42
Commandline: aptdaemon role='role-commit-packages' sender=':1.54'
Install: linux-image-extra-3.11.0-12-generic:amd64 (3.11.0-12.19), linux-image-3.11.0-12-generic:amd64 (3.11.0-12.19), linux-headers-3.11.0-12-generic:amd64 (3.11.0-12.19), mythtv-backend:amd64 (0.27.0+fixes.20131010.e59e5f6-0ubuntu0mythbuntu4, automatic), python-commandnotfound:amd64 (0.3ubuntu8), linux-headers-3.11.0-12:amd64 (3.11.0-12.19), python-gdbm:amd64 (2.7.4-0ubuntu1, automatic)
```

You can see that I uninstalled mythtv-backend but it re-installed itself on the next update.

---

### Post by tgm4883 on 2013-10-11
> **williammanda said:**
> This is the output from the var/log/apt:

```
Start-Date: 2013-10-10  13:46:19
Commandline: /usr/sbin/synaptic
Purge: mythtv-backend:amd64 (0.27.0+fixes.20131006.77db957-0ubuntu0mythbuntu4)
End-Date: 2013-10-10  13:46:26

Start-Date: 2013-10-10  13:56:42
Commandline: aptdaemon role='role-commit-packages' sender=':1.54'
Install: linux-image-extra-3.11.0-12-generic:amd64 (3.11.0-12.19), linux-image-3.11.0-12-generic:amd64 (3.11.0-12.19), linux-headers-3.11.0-12-generic:amd64 (3.11.0-12.19), mythtv-backend:amd64 (0.27.0+fixes.20131010.e59e5f6-0ubuntu0mythbuntu4, automatic), python-commandnotfound:amd64 (0.3ubuntu8), linux-headers-3.11.0-12:amd64 (3.11.0-12.19), python-gdbm:amd64 (2.7.4-0ubuntu1, automatic)
```

You can see that I uninstalled mythtv-backend but it re-installed itself on the next update.

Odd. Do you have mythtv-dbg installed? If so, if you remove that and also remove the backend package does it get reinstalled again?

---

### Post by williammanda on 2013-10-12
Yes mythtv-dbg is installed. It was installed along with mythtv-frontend automatically. It caught my eye when I first saw it but let it go...I had no idea it would lead to mythtv-backend.
I have uninstalled mythtv-dbg and mythtv-backend and did and update.....mythtv-backend wasn't suggested or installed. Seems to have fixed the problem but mythtv-dbg shouldn't be required as a dependency of mythtv-frontend.
Thanks

---

### Post by superm1 on 2013-10-13
> **williammanda said:**
> Yes mythtv-dbg is installed. It was installed along with mythtv-frontend automatically. It caught my eye when I first saw it but let it go...I had no idea it would lead to mythtv-backend.
I have uninstalled mythtv-dbg and mythtv-backend and did and update.....mythtv-backend wasn't suggested or installed. Seems to have fixed the problem but mythtv-dbg shouldn't be required as a dependency of mythtv-frontend.
Thanks
mythtv-dbg was intentionally made a "Recommends".  This causes it to be installed by default with most APT tools but can be removed.  It can also be prevented from being installed with --no-install-recommends.  This change was made so that in general the bug reports we received would be more beneficial.

It's an unfortunate side-effect that mythtv-backend was getting installed.  I'm a bit perplexed why that was happening in the first place because mythtv-frontend should have been able to resolve that dependency.  Could you comment on what APT frontend tool you were using that caused this behavior to happen?

Thanks,

---

### Post by williammanda on 2013-10-13
> **superm1 said:**
> Could you comment on what APT frontend tool you were using that caused this behavior to happen?Thanks,

synaptic

---

