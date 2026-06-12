---
title: "switching repos cobbled logging, does that count as a bug?"
date: 2012-03-15
forum: Mythbuntu
---

### Post by ricklous on 2012-03-15
Hello,

I recently took the plunge and switched from the 0.24.2 stable repo to the trunk/0.25 repo after the RC was released. All went well apart from the change to using syslog. The log files that already existed had their user and group set to mythtv/mythtv, meaning syslog couldn't write to them, and the freshly created log files had syslog/adm ownership. Once i'd read up in a bit more detail I tried this:

<code>
sudo chown -R --reference /var/log/mythtv/mythutil.log /var/log/mythtv
</code>

....which got things straightened out and the logging started straight away without anything needing to be restarted. 

I was wondering if this counts as a bug to be sorted during package install, or if its viewed as a quirk of switching from one branch to another?

---

### Post by superm1 on 2012-03-16
Yeah this looks like a bug.

mythtv-common's postinstall script has this snippet in it that is supposed to fix it for you.

    ```
#fix rsyslog permissions
    if [ -d "$dir" ] && ! dpkg-statoverride --list "$dir" >/dev/null; then
        chown syslog:adm -R /var/log/mythtv
        chmod 2755 /var/log/mythtv
    fi
```

Unfortunately "$dir" isn't defined anywhere.  I've fixed it in the packaging.  Should be reflected in autobuilds in a day or two.  In the future, file bugs for the packaging using this command:

```
# ubuntu-bug mythtv

```
Thanks!

---

