---
title: "How to correctly apply, remove and set up an Intel Pro/Wireless3954ABG for injection?"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-26
I am a relative newcomer to Ubuntu.
 So please bear this in mind when replying??

I know it is possible to apply a driver patch to my Intel pro/wireless 3945ABG Wireless card.
 That will allow packet injection to be implemented...

I was given the bellow commands to use to patch my wireless card with an appropriate driver.

But after running the below commands something is Not quite working as it should ??

Can someone help me to correctly use the below commands? 

Or even give me better ones to apply (if you spot any problems with the ones below).

  and in turn, help me to begin to have a better understanding of the Ubuntu Terminal and  moving between directories etc etc?

I think (But I am not totally sure) That the original default wireless driver is not being blacklisted, and is starting along with the newly applied desired driver when i restart Ubuntu??

I look forward to finaly getting to grips with this issue. It has been quite an enjoyable learning curve so far...

Here are the Commands I was given which I have had some success with:...


Open a terminal and type the following commands

sudo apt-get install build-essential (get core files)

sudo apt-get install libssl-dev (get supporting library)

wget [http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ip...022008.tar.bz2) (downloads driver)

tar -xjf ipwraw-ng* (extract the archive file)

cd ipwraw-ng (go to the extracted folder)

make (compile the source files into a binary)

sudo make install (install the driver)

sudo make install_ucode

echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)

sudo depmod -ae (create a dependency file for the modules)

sudo modprobe -r iwl3945 (unload driver that you do not need)

sudo modprobe ipwraw (load the driver that you installed)

sudo ifconfig wlan0 up (enable the network adapter)

When you're done, open a terminal and type lsmod, you should see the ipwraw driver loaded.

Should I turn my wireless card on/off before, or after using any of the given commands?

and also. Should I be rebooting Ubuntu at any key points to make sure the driver patches are installed correctly??

If so when should I be rebooting?

This is the first command i was shown to blacklist the original non suitable wireless driver:

    'echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)'

 Is this the correct command to blacklist the original driver??

 Also. Do I enter it into the terminal as it is shown. Or, Should it be entered into the terminal in two parts?  example:

      'echo "blacklist ipwraw" 

  and then:
                      'sudo tee /etc/modprobe.d/ipwraw'

Or should it be entered into terminal as:          
                                                                     echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw


I look forward to all replies, and thank-you in advance

---

### Post by MaDpOpPeT on 2009-09-03
I haven't seemed to get the driver to load however you don't need to do the echo command to blacklist drivers. Just type man modprobe....

---

