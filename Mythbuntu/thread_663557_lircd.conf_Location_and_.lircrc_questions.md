---
title: "lircd.conf Location and .lircrc questions"
date: 2008-01-10
forum: Mythbuntu
---

### Post by rswartze on 2008-01-10
I have lircd receiving commands from my remote fine.  I'm running 2 pvr150's but have not configured lirc for both, I'm letting it default to /dev/lirc0. The one pvr150 I tried did receive commands from the remote, but I haven't tried the second one yet.

But, I get the message "unknown remote: blaster" when I try to change channels (comand line testing). I'm using the standard change_channel.pl script very similar to this one [http://www.blushingpenguin.com/mark/lmilk/change_channel](http://www.blushingpenguin.com/mark/lmilk/change_channel).

I have put the 'blaster' remote into /etc/lirc/lircd.conf but it doesn't seem to find it after I restart lircd.  It's like I'm not editing the right file and it's using some config file from who-knows-where.  I even tried setting the /etc/lirc/lircd.conf explicitly in the /etc/lirc/hardware.conf file with no change.

I've previously had one of these pvr150's and the blaster workiing with the change_channel.pl script and this same 'blaster' remote configuration in knoppmyth. 

Here are some questions:
1. What lircd.conf file is used by my lircd?
3. The default /etc/lirc/hardware.conf specified a file 'hauppauge/lirc.conf.hauppage' , which is not present in /etc/lirc/. Where is this??
4. What are the .lircrc files in the home directories and does this have something to do with my problem?
5. Do I need 'blaster' codes in my .lircrc files?  For every user?

Here's the relevant config/scripts:

> #
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  frequency     56000


  begin raw_codes
    name 0
    2175729664
    name 1
    2175729665
    name 2
    2175729666
    name 3
    2175729667
    name 4
    2175729668
    name 5
    2175729669
    name 6
    2175729670
    name 7
    2175729671
    name 8
    2175729672
    name 9
    2175729673
    name POWER
    2175729674
    name CH_UP
    2175729679
    name CH_DOWN
    2175729680
    name CH_PREVIOUS
    2175729683
    name KEY_POWER
    2154627082
  end raw_codes

end remote


begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.6.6(animax) on Tue Apr 15 19:50:27 2003
#
# contributed by 
#
# brand: 				Hauppauge
# model no. of remote control: 
# devices being controlled by this remote: PVR 2/350
#

begin remote

  name  hauppauge_pvr
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Power                    0x00000000000017FD
          Go                       0x00000000000017FB
          1                        0x00000000000017C1
          2                        0x00000000000017C2
          3                        0x00000000000017C3
          4                        0x00000000000017C4
          5                        0x00000000000017C5
          6                        0x00000000000017C6
          7                        0x00000000000017C7
          8                        0x00000000000017C8
          9                        0x00000000000017C9
          Back/Exit                0x00000000000017DF
          0                        0x00000000000017C0
          Menu                     0x00000000000017CD
          Red                      0x00000000000017CB
          Green                    0x00000000000017EE
          Yellow                   0x00000000000017F8
          Blue                     0x00000000000017E9
          Ch+                      0x00000000000017E0
          Ch-                      0x00000000000017E1
          Vol-                     0x00000000000017D1
          Vol+                     0x00000000000017D0
          Ok                       0x00000000000017E5
          Mute                     0x00000000000017CF
          Blank                    0x00000000000017CC
          Full                     0x00000000000017FC
          Rewind                   0x00000000000017F2
          Play                     0x00000000000017F5
          Forward                  0x00000000000017F4
          Record                   0x00000000000017F7
          Stop                     0x00000000000017F6
          Pause                    0x00000000000017F0
          Replay                   0x00000000000017E4
          Skip                     0x00000000000017DE
      end codes

end remote


#
# this config file was automatically generated
# using lirc-0.7.0(any) on Sun Nov 28 20:25:09 2004
#
# contributed by 
#
# brand:   Hauppauge 350
# Created: G.J. Werler (The Netherlands)
# Project: Mythtv Fedora Pundit-R [www.mythtvportal.com](www.mythtvportal.com)
# Date:    2004/11/28
# model no. of remote control: Hauppauge A415-HPG
# devices being controlled by this remote: PVR-350
#

begin remote

  name  Hauppauge_350
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           969   811
  zero          969   811
  plead        1097
  gap          114605
  toggle_bit      2


      begin codes
          Go                       0x00000000000017BB
          Power                    0x00000000000017BD
          TV                       0x000000000000179C
          Videos                   0x0000000000001798
          Music                    0x0000000000001799
          Pictures                 0x000000000000179A
          Guide                    0x000000000000179B
          Radio                    0x000000000000178C
          Up                       0x0000000000001794
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Down                     0x0000000000001795
          OK                       0x00000000000017A5
          Back/Exit                0x000000000000179F
          Menu/i                   0x000000000000178D
          Vol+                     0x0000000000001790
          Vol-                     0x0000000000001791
          Prev.Ch                  0x0000000000001792
          Mute                     0x000000000000178F
          Ch+                      0x00000000000017A0
          Ch-                      0x00000000000017A1
          Record                   0x00000000000017B7
          Stop                     0x00000000000017B6
          Rewind                   0x00000000000017B2
          Play                     0x00000000000017B5
          Forward                  0x00000000000017B4
          Replay/SkipBackward      0x00000000000017A4
          Pause                    0x00000000000017B0
          SkipForward              0x000000000000179E
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Asterix                  0x000000000000178A
          0                        0x0000000000001780
          #                        0x000000000000178E
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
      end codes

end remote
#
# this config file was automatically generated
# using lirc-0.7.0pre4(serial) on Sun Oct  2 00:24:32 2005
#
# contributed by anton|ganthaler.at and juergen.wilhelm|aon.at
# members of linux user group Vorarlberg [www.lugv.at](www.lugv.at)
# 
# for ir remote controler from Hauppauge WinTV Nexus-S
# most of the keys are supported
#
# brand:                       Hauppauge
# model no. of remote control: WinTV Nexus-S
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge_WinTV_Nexus-S
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           944   828
  zero          944   828
  plead         980
  gap          113932
  min_repeat      1
  toggle_bit      2


      begin codes
          Up                       0x0000000000001794
          Down                     0x0000000000001795
          Left                     0x0000000000001796
          Right                    0x0000000000001797
          Power                    0x00000000000017BD
          Ok                       0x00000000000017A5
          Menu                     0x000000000000178D
          Back                     0x000000000000179F
          Red                      0x000000000000178B
          Green                    0x00000000000017AE
          Yellow                   0x00000000000017B8
          Blue                     0x00000000000017A9
          0                        0x0000000000001780
          1                        0x0000000000001781
          2                        0x0000000000001782
          3                        0x0000000000001783
          4                        0x0000000000001784
          5                        0x0000000000001785
          6                        0x0000000000001786
          7                        0x0000000000001787
          8                        0x0000000000001788
          9                        0x0000000000001789
          Play                     0x00000000000017B5
          Pause                    0x00000000000017B0
          Stop                     0x00000000000017B6
          Record                   0x00000000000017B7
          FastFwd                  0x00000000000017B4
          FastRwd                  0x00000000000017B2
          Channel+                 0x00000000000017A0
          Channel-                 0x00000000000017A1
          Volume+                  0x0000000000001790
          Volume-                  0x0000000000001791
          Mute                     0x000000000000178F
          Timers                   0x000000000000178A
          Recordings               0x000000000000178E
          Back                     0x000000000000179F
          Record                   0x00000000000017B7
          Pause                    0x00000000000017B0
      end codes

end remote


> #!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "blaster";

# Let's assume you don't need to press enter after you punch in a
# channel number. Change this to 1 if your cable box expects you press
# enter after each command
$needs_enter = 0;

# Change this to point to your rc executable
#$rc_command = "/usr/bin/irsend --device=/dev/lircd0";
$rc_command = "/usr/bin/irsend";

# This subroutine actually sends the signal to the cable box
sub change_SIGNAL {
    my($SIGNAL) = @_;
    system ("$rc_command SEND_ONCE $remote_name $SIGNAL");
}

$SIGNAL=$ARGV[0];
open F, ">> /var/log/channel.log";
print F "channel changing $SIGNAL\n";
close F;
print "channel changing $SIGNAL\n";

# Checks if $SIGNAL begins with a digit
# If it detects that the string is made up of digits, then it puts
# spaces between the digits.  Ex. 1234 becomes 1 2 3 4
if ( $SIGNAL =~ /^\d+$/ )
{
    my $length = length($SIGNAL);
    my $counter = 0;
    my $temp;

    # Send double previous to wake up the receiver if screen saver, seems
    # to need a kick to change properly every time
#    system("$rc_command SEND_ONCE $remote_name CH_PREVIOUS");
#    system("$rc_command SEND_ONCE $remote_name CH_PREVIOUS");
    while( $counter < $length )
    {
        $temp .= substr($SIGNAL,$counter,1) ." ";
        $counter++;
    }

    change_SIGNAL($temp);
    sleep 0.4
}
else
{
    # argument we passed was not made up of digits, so it must be a
    # command that does something other than channel changing on the
    # cable box
    change_SIGNAL($SIGNAL);
}

# Do we need to send enter
if ( $needs_enter )
{
    system ("$rc_command SEND_ONCE $remote_name ENTER");
}

> # /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_pvr150"

# Default configuration files for your hardware if any
#LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
LIRCD_CONF="/etc/lirc/lircd.conf"
LIRCMD_CONF=""

---

### Post by AlecJ on 2008-01-10
Hi you need to set the event number of the IR input and put it in the DEVICE="(here)".

Follow this link for the best how to I've found
[http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

---

### Post by williammanda on 2008-01-10
You can also use this link for help:
[https://help.ubuntu.com/community/InstallLirc/Gutsy](https://help.ubuntu.com/community/InstallLirc/Gutsy)

Thanks

---

