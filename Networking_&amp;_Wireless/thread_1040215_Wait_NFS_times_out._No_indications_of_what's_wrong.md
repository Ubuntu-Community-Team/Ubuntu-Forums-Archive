---
title: "Wait NFS times out. No indications of what's wrong...."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by rewolff on 2009-01-15
It seems that one of my NFS mounts isn't working. I've spent a couple of days being irritated waiting for the stupid timeout. I went into the correct /etc/... waitnfs script today, and found where the timeout happens... 

I added one line: 

        for mountpt in $waitnfs; do
                log_action_begin_msg "Waiting for $mountpt"

                while ! mountpoint -q $mountpt; do
                        sleep 0.1

                        TIMEOUT=$(( $TIMEOUT - 1 ))
                        if [ $TIMEOUT -le 0 ]; then
                                echo "Failed waiting for $mountpt"
                                log_action_end_msg 1
                                break
                        fi
                done

                if [ $TIMEOUT -gt 0 ]; then
                        log_action_end_msg 0
                fi

which should give me an indication about what mountpoint failed to come up. 

(I suspect I'm getting an immediate "permission denied" on one of the mounts, so waiting 90 seconds before continueing is kind of useless).

---

### Post by Archmage on 2009-01-15
Is the firewall turned on the PC where the NFS share is on? Try turning it off and try to reproduce this. The NFS port is VERY tricky.

---

