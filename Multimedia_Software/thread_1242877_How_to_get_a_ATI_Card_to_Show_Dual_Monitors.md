---
title: "How to get a ATI Card to Show Dual Monitors"
date: 2009-08-17
forum: Multimedia Software
---

### Post by stoneybroke on 2009-08-17
After building a new 64 bit computer with a Radeon HD 2400 XT Graphics card and installing Ubuntu 8.10 I like many others wanted to use 2 monitors that could run or display different programs or websites in each monitor. And as I also wanted to run 2 versions of Firefox (one on each monitor) another solution was needed.

After many day's searching various forums and modifying files with limited success, a simple solution to both problems was found.

I believe that regardless of what Radion ATI card you have (new or old) and regardless of what version of Ubuntu (or windows, or mac) you are using these instructions will work for them all, as you build the graphics controller around your system.

Don't be put off by this the procedure is very simple and virtually automated. 

The first thing you need to do is identify your card to do this enter this command at a terminal prompt;

lspci -nn | grep VGA

You should get something like this on the output;

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 2400 XT [1002:94c1]

The information you need is Radion HD 2400 XT or whatever your output says. Once you have this information you need to goto this website;

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Here you will see 3 windows, find your operating system in the first window, I.E Linux X86 for a 32 bit computer or Linux X86_64 for a 64 bit computer, then in the second window select your graphics card make, I.E Radion the third window will display all the model numbers, so select yours, mine is a ATI Radion HD 2400 series so I select that, then click the GO button.

This will then take you to the download page for the drivers, at this point before you go any further I recommend that you read the release notes and the Installer Instructions.

The Installer Instructions will guide you from here on what you need to do to get the driver configured to your system.

Once it is all set up you will now have 2 new GUI Interfaces under the Applications tab, one for normal uses and one for sys ops, that you can use to configure your monitors even if they are of different display sizes and types.

The next part is to get Firefox to work in both monitors, the problem is if you are already running Firefox you will get a error message saying that Firefox is already running. To get round this problem you need to set up a new user profile. Do not have Firefox running while doing this.

In a terminal window enter, firefox -ProfileManager you will be shown a window with the default profile, you need to create a new profile call it any name you like and save it. Then on your second monitor start firefox from the terminal window with the command firefox -p <whatever the name is> The -p will allow you to select a different profile for Firefox to run with.

Note:

There is a Firefox extension available called Profile Manager and Synchronizer that allows you to synchronize your tabs from one profile to another that is useful as well just search the Add-Ons for Firefox for it.

So that's it if all has gone as it should you should now have 2 monitors that can run 2 versions of Firefox or anything else you like.

Enjoy.

---

