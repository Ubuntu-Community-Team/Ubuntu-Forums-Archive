---
title: "Any way to recover or rollback to working wireless?"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by orb9220 on 2012-12-31
Was using default for my RTL8187 Wireless Adapter.

Was working but was disconnecting 2-6 times every 12 hrs. And not as robust and signal quality was in the 20%-30% less than windows version. Windows7 never lost connection and pages load faster.

And crappy nm-applet would drop connection then say connecting to Wpa connection and never succeed and start asking for the password which never worked clicking on ok. Requiring me to manual shut off and back on to make the connection.

So tried the windows version and it borked my wireless. To a state of No wifi in wireless section at all.

So how does one go about rolling back to a previous working tho less than stellar wifi driver?

Does linux have any way to recover revert back to what was working before? In the way of wireless,video,sound,etc??

And insights,explanations and reasons why linux doesn't have the ability would be appreciated.
.

---

### Post by ahallubuntu on 2012-12-31
What you describe (when wireless worked at all) would be unacceptable to me.  My wireless connections in Ubuntu are extremely solid.  I have a couple of Ubuntu-based computers and laptops.  I would never put up with that.

I'd start by googling for tips on Linux + your card.  There may be some settings you can change or a newer driver you can build for it.  You may even be able to replace the internal wireless card (not so much on an HP or Lenovo though because of the way they whitelist their wireless cards to limit which cards are allowed).  You could be able to swap out a wireless card for only $10 USD for a different/better one.  (I recommend Intel wireless cards - I've had excellent luck with them in Linux.)

As for the current state of "not working" - could be a problem of the state of the "wireless switch" (physical toggle switch) on the laptop.  I've heard of cases where you boot into Windows and somehow that messes up the sense of that switch.  There may be best known methods for getting it back to the way it was.  Maybe go back into Windows, turn the switch off and on or something (you didn't hibernate Windows did you?).  Or enter BIOS Setup and check for options regarding the wireless card (enable/disable)?  I'm sorry, I've never had this problem with my Dell laptops when switching between Windows and Ubuntu.

---

### Post by orb9220 on 2012-12-31
Well no laptop here. And it's an external usb with antennae.
Alfa AWUS036H USB wireless adapter. 

And the other issue is no adjusting Tx power as on windows side can jack up to it's rated 1000mw but not on linux side.

As my neighbor and I go in on halfsies on internet cost. Also there is a further Powell's Bookstore Free Wifi. 
On the window side can get both and no disconnects. And web sites load faster.

[Even tried this]("http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter") to make it more robust and still not up to windows snuff.

So was trying the window version and that's when I borked the wireless.
Had to do a complete system restore using [Redo Backup]("http://redobackup.org/") that I did 2 days ago. 
It restores complete partitions back to the way they were. And online again.

But really would like a easier solution then that when someone breaks wifi,video,etc... 
As there doesn't appear to be an easy way. 
Even read some solutions requires to be connected to the internet to resolve. 
Really No wifi and suppose to connect to the internet to fix how?
.

---

### Post by orb9220 on 2013-01-01
Hmmm a 100 views and a day and still no suggestions?
Was hoping something in the way of recovery or rolling back?
.

---

### Post by chadk5utc on 2013-01-01
I am unable to give you suggestions to resolve with current hardware but had same issues a couple years ago and decided to change to this device flashed with dd-wrt or stock work awesome and cover greater distance than anything previously purchased also increased the number of "visible" AP's in my rural area 10 fold.
[http://store.wisp-router.com/PicoM2HP-US](http://store.wisp-router.com/PicoM2HP-US) Simply configured the network to suit and plug into the eth0

---

### Post by captainskyhawk on 2013-01-01
Did you install Steam for Linux recently? I'm having the same issues with my 64-bit install of Ubuntu -- before this, it's been running rock-solid for months.  

Now, whenever I suspend my laptop, the wireless will not connect to the same router unless I reboot the router (though it's not a problem with the router, as no other computer/device on my network is having this issue, and nothing has changed with the router in over a year).

---

### Post by orb9220 on 2013-01-01
Thanks for the suggestion on replacing other devices. But not in the cards for me presently.

And to captainskyhawk if talking to me Nope no steam install. As pointed out trying to install windows wifi drivers with ndiswrapper. And failed leaving me no wifi. Had to do a system restore from Redo backup of hardrive.

I was hoping there was some other kind easier like with Windows that you can do partial restores or roll back a particular driver and such without require a full image restoring.

Just sounds like linux not very reliable or stable if you can't roll back to a previous state in my eyes. 

And reading about kernel breaking what was working regressions or upgrades breaking things all the time for a lot of folks.
.

---

### Post by captainskyhawk on 2013-01-01
Yeah -- there is a way to rollback a certain package (driver, etc.) in Ubuntu using the Synaptic Package Manager (you can force older versions), however no easy one-click message like a System Restore on Windows (which I'd like too, to be honest).  

You can try looking in the logs (there's only a few) in /var/log/apt/ to see what was installed in the past few days, and then trying to selectively downgrade a few packages in Synaptic, but it's hard to say what will work. I'm currently trying this right now without much luck.

I feel you on problem about updates breaking things on Linux -- it's a big, big, big problem.  There simply isn't the money or the people working on the project to do serious regression testing like I'm sure Microsoft performs for a Windows update they roll out.

---

### Post by captainskyhawk on 2013-01-02
Looks like I fixed my problem, if it's any help -- looks like it was the "x-swap" advanced video card drivers (Steam recommends that you install them when you install Steam for Linux).  When I got rid of the repository, and forced a downgrade of the Intel-associated drivers package, my wireless works again upon restoring from a suspended state.

---

