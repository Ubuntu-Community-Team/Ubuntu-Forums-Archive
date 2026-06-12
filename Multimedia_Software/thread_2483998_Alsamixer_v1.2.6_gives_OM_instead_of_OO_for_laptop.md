---
title: "Alsamixer v1.2.6 gives OM instead of OO for laptop speakers"
date: 2023-02-14
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-02-14
How do I keep Alsamixer from putting "OM" in the (built-in) speaker column instead of "OO".  The "M" key is supposed to change this, but it will not.

Alsamixer version is 1.2.6 running under Ubuntu 22.10.

Thank you,

John

---

### Post by cigtoxdoc on 2023-02-19
I received a reply to my post that did not show up on this website.  Here is this message:

Here is the message that has just been posted:
***************
I put your question to Chat AI and this is what it came up with:

The "OM" in Alsamixer's speaker column stands for "Muted Left and Right Channels." This means that the sound is currently muted and not playing through the built-in speakers. In order to change it to "OO," which stands for "Unmuted Left and Right Channels," you can follow these steps:


1. Open Alsamixer by typing "alsamixer" in the terminal.
2. Use the arrow keys to navigate to the speaker column.
3. Press the "M" key to toggle between "OM" and "OO". If the "M" key does not work, try using the "Space" key instead.
4. If the "M" or "Space" key still does not work, check if there are any conflicting key bindings in your system settings. You can try to reset the key bindings for Alsamixer or assign a different key for muting/unmuting.
5. If the above steps do not work, try updating Alsamixer to the latest version or reinstalling it.

However, that solution did not fix the problem.  I hope the moderators and other experts will stop ignoring the laptop sound problem and provide short-term workarounds and get the problem software rewritten. I have done much troubleshooting.  I hope the experts will read the terminal output shown below:  Thank you, John

john@john-Precision-7720:~$ sudo touch /usr/share/pipewire/media-session.d/with-pulseaudio
[sudo] password for john: 
john@john-Precision-7720:~$ systemctl --user restart pipewire-session-manager
john@john-Precision-7720:~$ systemctl --user enable pulseaudio
john@john-Precision-7720:~$ 
systemctl --user start pulseaudio
Job for pulseaudio.service failed because the control process exited with error code.
See "systemctl --user status pulseaudio.service" and "journalctl --user -xeu pulseaudio.service" for details.
john@john-Precision-7720:~$ systemctl --user status pulse.service
Unit pulse.service could not be found.
john@john-Precision-7720:~$ systemctl --user status pulseaudio.service
× pulseaudio.service - Sound Service
     Loaded: loaded (/usr/lib/systemd/user/pulseaudio.service; enabled; preset: enabled)
     Active: failed (Result: exit-code) since Sun 2023-02-19 09:24:45 EST; 2min 57s ago
TriggeredBy: × pulseaudio.socket
    Process: 12353 ExecStart=/usr/bin/pulseaudio --daemonize=no --log-target=journal (code=exited, status=1/FAI>
   Main PID: 12353 (code=exited, status=1/FAILURE)
        CPU: 14ms

Feb 19 09:24:45 john-Precision-7720 systemd[1312]: pulseaudio.service: Scheduled restart job, restart counter i>
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: Stopped Sound Service.
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: pulseaudio.service: Start request repeated too quickly.
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: pulseaudio.service: Failed with result 'exit-code'.
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: Failed to start Sound Service.

john@john-Precision-7720:~$ journalctl --user -xeu pulseaudio.service
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: Stopped Sound Service.
&#9617;&#9617; Subject: A stop job for unit UNIT has finished
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A stop job for unit UNIT has finished.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 987 and the job result is done.
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: pulseaudio.service: Start request repeated too quickly.
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: pulseaudio.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit UNIT has entered the 'failed' state with result 'exit-code'.
Feb 19 09:24:45 john-Precision-7720 systemd[1312]: Failed to start Sound Service.
&#9617;&#9617; Subject: A start job for unit UNIT has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit UNIT has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 987 and the job result is failed.
lines 226-248/248 (END)

---

