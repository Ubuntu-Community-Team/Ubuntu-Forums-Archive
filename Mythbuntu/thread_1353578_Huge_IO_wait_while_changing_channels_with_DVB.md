---
title: "Huge IO wait while changing channels with DVB"
date: 2009-12-12
forum: Mythbuntu
---

### Post by asbjorn on 2009-12-12
For several days I've been trying to find out why my system more or less are coming to a halt while changing channels in Mythbuntu 9.10 AMD64. I finally found that mythbackend are writing thousands of vdpau errors to the logfile /var/log/mythtv/backend.log.
<snip>number of reference frames exceeds max<snip>

To make them go away, I used syslog-ng.

1) create a fifo file: mkfifo /var/log/mythtv/mythbackend.fifo

2) Edit /etc/default/mythtv-backend like this:
# User as which to run
USER=mythtv
# Replace all arguments to mythtv-backend
#ARGS="--logfile /var/log/mythtv/mythbackend.log"
ARGS="--logfile /var/log/mythtv/mythbackend.fifo"

3) install syslog-ng

4) edit syslog-ng config file and add the following
source mythback-s {
        pipe("/var/log/mythtv/mythbackend.fifo");
};
destination mythback-d {file("/var/log/mythtv/mythbackend.log");};
filter vdpau-errors {not match("number of reference frames exceeds max");};
log {
        source(mythback-s);
        filter(vdpau-errors);
        destination(mythback-d);
};

5) Set owners on logfiles:
chown root.mythtv mythbackend.log
chown mythtv.mythtv mythbackend.fifo

6) Restart syslog-ng

7) Restart mythtv-backend

/Asbjorn

---

