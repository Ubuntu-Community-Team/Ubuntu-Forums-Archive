---
title: "How to do a special purpose install of Sun Java for Vuze"
date: 2008-12-02
forum: Multimedia Software
---

### Post by VuzeLover on 2008-12-02
[b][color=red]WARNING!! THIS CUSTOM SPECIAL PURPOSE INSTALL OF SUN JAVA IS ONLY MEANT FOR VUZE THE BITTORRENT CLIENT.
THIS SPECIAL INSTALL WILL PROBABLY NOT WORK WITH OTHER SOFTWARE.[/color][/b]

**[color=red]THIS DOES NOT INSTALL THE JAVA PLUGIN.  WE DON'T WANT IT FOR THIS CUSTOM INSTALL.[/color]**




[b][color=green]Target audience is...
Users who run the built in tracker and or the built in web-site web server.
Users who run a headless Vuze seed box or content distribution system.
Users who need a high degree of control over permissions and who need to minimize the amount of software installed on the system.[/color][/b]

**[color=green]Tested on Ubuntu 8.10, should work on Debian Lenny but I am unable to test Lenny at the moment.  Will test Lenny later[/color]**
[b][color=green]Tested with my other howto guide in mind [here]("http://ubuntuforums.org/showthread.php?t=995327").
But should work with the Ubuntu and Debian Vuze repositories versions[/color][/b]




**[color=green]Inspired by this web site [here]("http://gaveen.owain.org/2008/03/setup-sun-java-on-linux-manually.html").[/color]**
**[color=green]Ready![/color]**




**Step 1**
**[color=red]WARNING REMOVING EXISTING SUN JAVA WILL PROBABLY MAKE ANY CURRENTLY INSTALLED JAVA SOFTWARE STOP WORKING[/color]**.
If you have Vuze and Sun Java currently installed from the official Ubuntu or Debian repositories, please remove the software.
I would prefer that you purge when removing the software as purging also removes configuration files.
Example using aptitude...
```
aptitude purge **Name of the software you are removing**
```
Example using Synaptic...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94982&stc=1&d=1228223316[/IMG]








**Step 2**
Download Sun Java [**[color=green]Here[/color]**]("http://java.sun.com").

Currently the web site is listing the Java on the right side of the page in the column labeled **"Popular Downloads:"**.
**[color=green]Select "Java SE".[/color]**
**[color=green]Select "Java SE Runtime Environment (JRE)" (currently this is 6 Update 11)[/color]**
A new web page will appear where you need to select your proper OS.  Select 1 of 3 choices.
**[color=green]Linux 32bit (32bit is simply labeled Linux)[/color]**
**[color=green]Linux 64bit[/color]**
**[color=green]Linux Itanium[/color]**
Most users will select the Linux 32bit or Linux 64bit.

You will come to a new page that gives you 2 choices of file formats.
Select the self extracting **[color=red]bin[/color]** file format.
**[color=red]Do not select the RPM[/color]**








**Step 3**
Open a terminal and change location to where you downloaded the file.
```
cd **[color=green]Location of file[/color]**
```
Make the file executable...
```
chmod +x **[color=green]Name_of_file[/color]**
```
Extract the downloaded file.
Currently for 32bit it is...
```
./jre-6u11-linux-i586.bin
```
And currently for 64bit it is...
```
jre-6u11-linux-x64.bin
```
Keep in mind Sun will update Java from time to time and as a result the file names will change.
When you execute the install command you will get a license agreement.  Press the space bar until you come to the yes or no question.
Enter yes as a simple y will not do the trick.
If you answered yes then at this point Java will be extracted into a folder that is the same name as the file.
For example, if you extract the 64 bit file then you get the folder "**jre1.6.0_11**".








**Step 4**
Move the newly created folder from step 4 into the folder "/opt/".
Open a terminal.
As an example for 64bit you would do...
```
sudo mv jre1.6.0_11 /opt/
```
Remember to use the actual folder name that was created on your computer.
Your folder structure should now be, as an example for 64bit "/opt/jre1.6.0_11/".








**Step 5**
Create a dedicated secure user account for Sun Java.
Open a terminal.
```
sudo adduser --home /opt/**[color=red]CHANGE_ME_TO_JAVA_FOLDER_NAME_IN_OPT[/color]** --shell /bin/false --no-create-home --disabled-login sunjava
```
As an example for 64bit Java, sudo adduser --home /opt/jre1.6.0_11 --shell /bin/false --no-create-home --disabled-login sunjava.  I should mention that this simply puts the files and folders under a non-root account. The Sun Java process however will still run as the user who called Sun Java. I have not found a good method yet for running the Sun Java process as the Sun Java user. The annoying but simple method is to put Sun Java and Vuze under the same user and group and then do "--home /home/vuze". Then you would enter a password and use the user switching applet to switch to the Vuze user.








**Step 6**
Change the permissions to the dedicated user that we created in step 5.
Open a terminal.
```
sudo chown -R sunjava:sunjava /opt/**[color=red]CHANGE_ME_TO_THE_JAVA_FOLDER_NAME_IN_OPT[/color]**/
```
Remember to put the colon in between the user names.








**Step 7**
Make the newly installed Sun Java available to Vuze.
Open a terminal.
To make the Java available to all users system wide...
```
sudo nano /etc/profile
```
Add or copy and paste the following 2 lines into the profile file at the very bottom.
> PATH=/opt/**[color=red]THE_NAME_OF_THE_JAVA_FOLDER_IN_OPT[/color]**/bin:$PATH
export PATHTo exit press Ctrl x and press y then enter to save the file.




To make the Java available on a per user basis...
```
nano .bashrc
```
Add or copy and paste the following 2 lines into the .bashrc file at the very bottom.
> PATH=/opt/**[color=red]THE_NAME_OF_THE_JAVA_FOLDER_IN_OPT[/color]**/bin:$PATH
export PATHTo exit press Ctrl x and press y then enter to save the file.
**[color=red]IN ORDER FOR THESE 2 FILES TO TAKE EFFECT YOU MUST LOGOUT OF YOUR DESKTOP AND LOG BACK IN[/color]**.
You might think that doing this on a per user basis would be better security.  Well it's not as long as any user can see Java in /opt and simply add it to their .bashrc.  The per user is only convenient where you want control over what uses Sun Java.







**Step 8**
You are now ready to rock!  However I strongly recommend that you follow my Vuze howto guide [**[color=green]here[/color]**]("http://ubuntuforums.org/showthread.php?t=995327").
Of course you can use the repositories to install Vuze but I think it is much better to follow my howto guide.

---

