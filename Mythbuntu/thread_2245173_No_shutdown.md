---
title: "No shutdown"
date: 2014-09-21
forum: Mythbuntu
---

### Post by drifting on 2014-09-21
Hi chaps
Just did an upgrade as well as a clean install of mythbuntu 14.04 with all the updates for OS and myth .27 mythbuntu repo.
Why now has the old problem of not shutting down reared it's head again?
More importantly how can I make shutdown work? Exit works I might add. Machine acer revo which up to now has been a gem.

---

### Post by khPWXxF on 2014-09-23
Would you like to give more information?
Frontend? Back end? Myth welcome?
what mechanism do you expect to be invoked to shut down?
Phil

---

### Post by drifting on 2014-09-23
Hi Phil

Sorry that was rather terse on my part. I was referring to the frontend. As for mechanism, not sure what you mean? Apart from wanting the Mythbuntu to shut down when I press shutdown? This works on a stock install of Mythbuntu 12.* Fine, as I just tried it, but on 14.4 it does nothing. Exit works and I get get to the desktop and shutdown from the logoff . Also sudo shutdown works too. Do no use Mythwelcome.
My comment about this rearing it's head again, was that this used to occur on the frontends of a much earlier versions, and for the life of me I cannot think how I made it work, have a feeling it was giving rights to shutdown to the myth user?

Regards Paul.

---

### Post by khPWXxF on 2014-09-23
Paul,
Sorry if I'm being obtuse.
Are you saying that it's a frontend only system with a separate backend? That when you power it on it shows the main mythtv frontend screen?
You expect it to close down when you press 'shutdown'. Where is that button? On your remote?
Phil

---

### Post by rmnelson on 2014-09-24
I believe I'm having the same problem on a frontend only without mythwelcome. Started with mythbuntu 12.04 mythtv .27, upgraded to mythbuntu 14.04 mythtv .27. Pressing the "exit" key on the remote from mythfrontend pops up a "Do you really want to exit MythTV?" and three options; "No" "Yes, Exit Now", and "Yes, Exit and Shutdown". On 12.04 each option did exactly what it said, that is you could either cancel your exit by selecting "No", exit to the mythbuntu desktop, or exit and shutdown the frontend computer. Now on 14.04, with no changes whatsoever to mythtv, only the "No" and "Yes, Exit Now" options work. Selecting "Yes, Exit and Shutdown" neither exits nor shuts down. I would like to be able to select "Yes, Exit and Shutdown" and have both of those things happen exactly as they did under 12.04/.27. Any ideas? Thanks!

---

### Post by khPWXxF on 2014-09-26
does the field on the configuration page at frontend >setup > general > page 8 help you?
Phil

---

### Post by topcat5 on 2014-09-26
> **rmnelson said:**
> .....Now on 14.04, with no changes whatsoever to mythtv, only the "No" and "Yes, Exit Now" options work. Selecting "Yes, Exit and Shutdown" neither exits nor shuts down. I would like to be able to select "Yes, Exit and Shutdown" and have both of those things happen exactly as they did under 12.04/.27. Any ideas? Thanks!

What you are describing, is not enabled by default.  You have to go to the setup screen for the FE and change it so that it offers up this option as well.  A reinstall to the new version, if you jumped from 12 to 14 seems to set it back to the default.   

I suppose they do it this way because you would not want to present this option to a user if the FE was also on the same machine as the BE.  I had to re-enable it on the two dedicated FEs that I have, when I recently upgraded.

---

### Post by rmnelson on 2014-09-27
I have 3 myth installs that I just updated from 12.04/.27 to 14.04/.27, one FE/BE and two FE only. Two of the installs are on identical intel core 2 duo mac minis, and the third is a c2d imac. All are running mythbuntu natively with identical frontend setups and a single remote setup for all three. On two of them, the FE/BE and one of the FE only machines, the Exit/Shutdown menu continued to work exactly as before upgrade with no additional configuration in Myth whatsoever. The third required a bunch of reconfiguration including the Exit/Shutdown fix. So on the one that required additional work page 8 of Setup/General now shows a command in "shutdown" that I entered after the upgrade, and I had to edit sudoers to get it working again. The other two show no command in the "Shutdown" window and work as they did before the upgrade to 14.04. Just for interest I changed from the "default" setting on the FE/BE and added the shutdown menu item to the exit menu. It worked without any additional configuration by me. I have now reset the FE/BE to default since clearly I don't want to mistakenly shutdown the running BE. But I'm still left wondering why 3 essentially identical installs required different configuration after upgrading to 14.04. For me all is working as I want now, so this is just academic interest. But my experience with my three machines before this upgrade to 14.04 is that the exit menu when set on page 8 of Setup/General to "default" did shutdown the machine without any configuration by me, and on two of the three this behavior continued after the upgrade.

---

### Post by khPWXxF on 2014-09-29
This may not be relevant to your specific issue but you should be aware that there is another 'tweak' in frontend setup which affects this area of closedown.
I'm not at my Myth box at present but from memory it's called Key bindings or edit keys. Scroll down to find 'main menu'. There's the option to set the keys to exit or to give exit prompt. Default is 'exit prompt' which is not what is wanted in (say) a welcome setup. This caused puzzlement when it was introduced between 9.10 and 12.04 but the settings are included in a backup and so should have transferred with your database import.
Phil

---

### Post by drifting on 2014-09-30
> **khPWXxF said:**
> Paul,
Sorry if I'm being obtuse.
Are you saying that it's a frontend only system with a separate backend? That when you power it on it shows the main mythtv frontend screen?
You expect it to close down when you press 'shutdown'. Where is that button? On your remote?
Phil

Not at all, and yes it is the frontends only, not the backend, that stays on permanently. And I usually navigate the menu and select exit and shutdown. I wonder what the shutdown fix mentioned earlier was? I have gone into the key settings, and they match on both my frontends (one has 12, the other 14 Mythbuntu) and with the settings as suggested changed to Default.

Paul

---

### Post by khPWXxF on 2014-09-30
This doesn’t answer the question of why it’s not behaving as expected, but if you want a sledgehammer to crack a nut then could you find how frontend is started up when you power up?
eg in    Applications > settings > session and startup
 
Then modify that to a ‘wrapper’ script something like this:
```
#!/bin/bash
mythfrontend –service
sudo shutdown –h now
```

Phil

---

### Post by drifting on 2014-10-01
> **khPWXxF said:**
> This doesn’t answer the question of why it’s not behaving as expected, but if you want a sledgehammer to crack a nut then could you find how frontend is started up when you power up?
eg in    Applications > settings > session and startup
 
Then modify that to a ‘wrapper’ script something like this:
```
#!/bin/bash
mythfrontend –service
sudo shutdown –h now
```

Phil

Surely would that not require a password? Not easy with a remote.
Think I shall just leave the frontends on 12, there is little advantage at the moment for upgrading to 14 as I can see, only grief from the family moaning at me that they cannot turn it off. (Came home to 3 TV's with XFCE desktop!)

Paul.

---

### Post by rmnelson on 2014-10-01
Here's what I did  to get the exit/shutdown menu working again in my FE. Shamelessly copied from a number of sources, and I make no claim to be any kind of linux expert. This may be the dumbest way to do this; in fact it probably is the dumbest way to do it. But it works and now my remote can shutdown the frontend machines.

#open new sudoers file (I didn't have any, so I picked this name at random).
sudo visudo -f /etc/sudoers.d/mythtv 

#paste this in, save, quit
%mythtv ALL = NOPASSWD: /sbin/shutdown

Then I added /sbin/shutdown to the "shutdown" menu page 8 of General, and the FE machine shuts down when asked.

---

### Post by drifting on 2014-10-03
> **rmnelson said:**
> Here's what I did  to get the exit/shutdown menu working again in my FE. Shamelessly copied from a number of sources, and I make no claim to be any kind of linux expert. This may be the dumbest way to do this; in fact it probably is the dumbest way to do it. But it works and now my remote can shutdown the frontend machines.

#open new sudoers file (I didn't have any, so I picked this name at random).
sudo visudo -f /etc/sudoers.d/mythtv 

#paste this in, save, quit
%mythtv ALL = NOPASSWD: /sbin/shutdown

Then I added /sbin/shutdown to the "shutdown" menu page 8 of General, and the FE machine shuts down when asked.


Thanks will give that a try. Still does not answer why it works on 12 but not 14, but hey ho, minor in the great scheme of things.

Regards Paul.

---

