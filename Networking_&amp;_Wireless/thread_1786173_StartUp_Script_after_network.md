---
title: "StartUp Script after network"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by VoyezScout on 2011-06-19
Hi,

************************
EDIT: I already found the solution. Fix is written at the end
************************
I have a strane requirement which I cannot manage to resolve, so I need to ask for some help:

I have an Ubuntu Server 10.04 installation, configured to be "On Lan Awaken", an with several users who may use it.
For electricity saving and maintainance reasons, I wrote a script which does the following:
 - Every ten seconds it executes the users command
    - If no users are found it does nothing
    - If a user is logged in and it is me, it ends the script
    - If a user is found and it is NOT me, it sends me a notification e-mail and ends the script
 - After 30 loop executions (so, after five minutes) and if no users have been found at all it sends me a notification e-mail and halts the system.

Now, the script runs properly without issues (executed manually and as a cron job), but I cannot manage to run it at startup.

I already tried the following:
- Setting the script into /etc/init.d/ folder and using update-rc.d to register it as a startup job. The result was that the script blocked the boot up process, and after five minutes it halted the system before networking had been started and anyone could have logged in. (I had to start the server locally and in recovery mode to fix the issue).
- Putting the script into the /etc/network/if-up.d folder: The script works as expected, but hostname is not registered into the DNS (aka the router) until I log in using the IP and the script is finished. So, it sound like it being executed before networking is completely started. A part from this, if I restart the networking at any time, the script is run again, which is not the exepected behavior.

So, the question is: How can I configure the script to be run only at startup and right after everything else have been executed? (so, executing it once users are able to log in normally).

Thanks in advance!

********************************
EDIT: Sometimes is not just aboug googling (I had searched a lot), but about looking for the right thing:
To FIX the issue, I just had to configure the right priority in the upate-rc.d command instead of using defaults:

update-rc.d ScriptName start 99 2 3 4 5 .

********************************

Voyez

---

### Post by Cheesehead on 2011-06-19
Upstart replaced the old sysvinit a few years ago. The /etc/rc*.d scripts still work, but are slowly being migrated to Upstart.

To use Upstart to listen for network-up and then run a job or start a daemon, create a file (or link) in /etc/init. For this example, let's call it /etc/init/my-network-up.conf
```
# 'my-network-up.conf' - My custom upstart events
#
# These are the scripts that run when a network appears.

description "My custom upstart events"

start on net-device-up     # Start a daemon or run a script
stop on net-device-down  # (Optional) Stop a daemon, scripts already self-terminate.

script
# You can really put shell script in here, including if/then and tests.
/path/to/myscript1
/path/to/myscript2
end script

```

You can also run a script upon network-up by placing it (or a link) in the /etc/networking/if-up.d directory...in fact, you can see the Upstart net-device-up emitter in there.

I use a net-device-up listener and a net-device-down listener to mount/unmount network drives, assign default network printers, add/remove network-related cron jobs, and much more.

---

