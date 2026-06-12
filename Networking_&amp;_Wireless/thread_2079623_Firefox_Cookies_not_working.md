---
title: "Firefox Cookies not working"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by Hotel on 2012-11-02
Hi
I'm having a weird problem with Firefox, a number of sites are reporting cookies are disabled and not letting me log in. 
The sites include:
[http://slashdot.org/]("http://slashdot.org/")
[http://web3.karabar-h.schools.nsw.edu.au/moodle/login/index.php]("http://web3.karabar-h.schools.nsw.edu.au/moodle/login/index.php")
The two sites are completely unrelated and I can still log into other sites such as this one and Facebook. Cookies are enabled in my settings.

The Page Info window list a number of cookies on both pages.
 

So far I've tried unsuccessfully:
-Clear History
-Clear Cache
-Deleting cookies.sql from the profile folder
-Deleting the cache and offline cache folders from the profile folder
-Creating and using a new user profile (via Firefox -P)
-Reinstalling firefox (via sudo aptitude reinstall firefox)
-Right Click on page>Page Info>Permissions and specifically allowing cookies for that site.
-Disabling EFFs 'HTTPs everywhere' add-on 

I considered running an 'apt-get purge firefox', but I really don't want to lose all my bookmarks and stored passwords.

I'm running firefox 16.0.2 and the latest version of kubuntu. 

Any help would be much appreciated,
Harry

---

### Post by vasa1 on 2012-11-02
Do you use "Privacy" extensions such as Ghostery? Maybe an update of a list is causing the problem? Even an update to a list used by Adblock Plus could cause the issue.

Do you have a problem if you run Firefox in [safe mode]("http://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode")?

---

### Post by Hotel on 2012-11-02
Thanks for the suggestion, I still have the problem running Firefox in safe mode though and the only privacy extension I use is HTTPs Everywhere, which I had already checked.

---

### Post by Hotel on 2012-11-03
Any other ideas, I've tried everything I can think of or can find on the Internet :(

---

### Post by SeijiSensei on 2012-11-03
Whenever I have a problem like this, I try rebuilding my firefox configuration.

The configuration is stored in a "hidden" directory called .mozilla (note the leading dot) in your home directory.  By default you won't see this directory if you list your home directory or display its contents in a file manager.  In a program like Dolphin or Nautilus there will be a switch in the settings to display the hidden files and directories.  If you flip that, you'll see a bunch of things appear that all begin with dots. 

Close firefox completely with File > Quit, then rename .mozilla to .mozilla.bad.  Now restart firefox.  It will rebuild your configuration with the defaults.  Do you still have the same problem with cookies?

If you're comfortable with the command line, you can simply type "mv .mozilla .mozilla.bad" at the prompt after closing firefox.  To see hidden directories from the command line, you need to add the "-a" option to ls.  For instance, the command "ls -la" will list all the files, both hidden and visible, in the long format with dates and permissions.

If the problem is fixed, you might want to restore your bookmarks.  The new firefox configuration will be stored in .mozilla/firefox/[something].default.  The "[something]" is an arbitrary string of letters and numbers.  For instance, my firefox configuration is stored in .mozilla/firefox/sgmwudb4.default.

In that directory there is a subdirectory called "bookmarkbackups" that contains daily backup of your bookmarks.  If you go to Bookmarks > Show All Bookmarks in firefox, you can  use the Import and Backup option.  Choose "Restore" then "Choose File".  Navigate to $HOME/.mozilla.bad/[something].default/bookmarkbackups and pick the most recent .json file there.

---

### Post by Hotel on 2012-11-06
Thanks, that still didn't work, I also tried 'sudo apt-get firefox* purge' and reinstall and that didn't fix it either, I can log into these sites from other locations. I also found another site that it is a problem for: edmodo.com

---

