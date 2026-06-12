---
title: "How I set up MythTV to change channels on my external Bell Dish Receiver"
date: 2008-03-16
forum: Mythbuntu
---

### Post by freymann on 2008-03-16
In under an hour, I now have my MythTV server changing channels on my external Bell Dish 4700 Reciever using the MCE remote/blaster that came with my PVR-150.

This web page was a great start:

[https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script)

I've been researching this for over a week which started when I was struggling with LinuxMCE (which didn't like the MCE remote transceiver I guess) so I already a file downloaded that I appended to /etc/lirc/lircd.conf. 

```

begin remote

#  name 3100
  name SAT_301
  bits           16
  flags SPACE_ENC
  eps            30
  aeps          100

  header        400  6100
  one           400  1700
  zero          400  2800
  ptrail        400
  gap          6200
  min_repeat      4
  toggle_bit      0

  frequency    56000

      begin codes
          info                     0x0000000000000000
          power                    0x0000000000000800
          play                     0x0000000000000C10
          1                        0x0000000000001000
          2                        0x0000000000001400
          3                        0x0000000000001800
          frwd                     0x0000000000001C10
          4                        0x0000000000002000
          5                        0x0000000000002400
          6                        0x0000000000002800
          menu                     0x0000000000002C00
          7                        0x0000000000003000
          8                        0x0000000000003400
          9                        0x0000000000003800
          ffwd                     0x0000000000003C10
          select                   0x0000000000004000
          0                        0x0000000000004400
          cancel                   0x0000000000004800
          guide                    0x0000000000005000
          mute                     0x0000000000005401
          cancel2                  0x0000000000005800
          right                    0x0000000000006000
          vol+                     0x0000000000006401
          up                       0x0000000000006800
          prev                     0x0000000000006C00
          left                     0x0000000000007000
          vol-                     0x0000000000007401
          down                     0x0000000000007800
          rec                      0x0000000000007C00
          pause                    0x0000000000008000
          stop                     0x0000000000008400
          sys_info                 0x0000000000009000
          *                        0x0000000000009800
          rew                      0x000000000000C410
          fwd                      0x000000000000C810
      end codes

end remote

```

 As instructed, I just added that to the end of /etc/lirc/lircd.conf and restarted lirc

sudo /etc/init.d/lirc restart

Typing this in the shell

irsend LIST SAT_301 &#8220;&#8221;

gave me a list of the commands lirc knows about. Kewl.

From here, the info on the page link above gives you the rest.

My 4700 Bell dish receiver doesn't understand the ch+ command, so I edited the change_channel.pl script a little to work under my requirements. Also note if you cut and paste his python or perl script, you need to make 2 changes in his script to change DCT700 to SAT_301

I'm not sure if the "sleep" program was on MythBuntu box either. I used synaptic software manage to add sleep??? and found a /bin/sleep. I edited the original author's sleep to use this path.

Here's the change_channel.pl script I'm using:

```

#!/usr/bin/perl -w
############################################################
# File -            channelchange.pl
# Author -          Guardian Bob
# Date -            Tuesday, August 07, 2007
# E-Mail -          Guardian.Bob@gmail.com
# Description -     Changes channels, working around the 
#                   broken 0
# Changelog -       August 07, 2007
#                   Initial Revision
#                   August 19, 2007
#                   Adjusted the sleep (0.2->0.3) as at
#                   0.2, two 5 commands were treated as one.
#                   Starting each channel change with a
#                   right to try to bring the box out of
#                   a standby mode (sometimes the box 
#                   ignores the first command sent.)
############################################################
use strict;

use constant IRCMD => "/usr/bin/irsend SEND_ONCE SAT_301 ";

# 0.2 is too short, will see 551 as 51
use constant SLEEPCMD => "/bin/sleep 0.3; ";

my %chanmap = ReturnChanMap();
sub ChannelCmd
{
    my $chan = shift();
    if(length($chan)==0)
    {
        return IRCMD . "select; ";
    }
    my $digit = substr $chan,0,1,"";
    return IRCMD. $digit . "; " . SLEEPCMD . ChannelCmd($chan);
}

my $channel = int($ARGV[0]);
my $cmd;
$cmd = ChannelCmd($channel);

# Build the cmd and print it
# Add the right command and wait a second to process it, as the box can
# sometimes ignore the first command sent.
exec $cmd;

# This is down here to try to separate the data from the code.
#
# While I don't like it, this is actually the best way,
# as the SAT_301 will skip channels.  Do not list an OnDemand
# channel as a substitute, not only will it lock the box for
# a few seconds, the up down will continue from the previous
# channel.  That said, using right/- through OnDemand channels
# will not demonstrate the same behavior.
sub ReturnChanMap
{
    return (
#   Chan      Sub,  Extra Commands ...    
    '10'  => [  '9', 'right' ],
    '20'  => [ '19', 'right' ],
    '30'  => [ '29', 'right' ],
    '40'  => [ '39', 'right' ],
    '50'  => [ '49', 'right' ],
    '60'  => [ '59', 'right' ],
    '70'  => [ '69', 'right' ],
    '80'  => [ '79', 'right' ],
    '90'  => [ '89', 'right' ],
    '100' => [ '99', 'right' ],
    '101' => [ '99', 'right', 'right' ],
    '102' => [ '99', 'right', 'right', 'right' ],
    '103' => [ '99', 'right', 'right', 'right', 'right' ],
    '104' => [ '99', 'right', 'right', 'right', 'right', 'right' ],
    '105' => [ '99', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '106' => ['111', 'left', 'left', 'left', 'left', 'left' ],
    '107' => ['111', 'left', 'left', 'left', 'left' ],
    '108' => ['111', 'left', 'left', 'left' ],
    '109' => ['111', 'left', 'left' ],
    '110' => ['111', 'left' ],
    '120' => ['119', 'right' ],
    '130' => ['129', 'right' ],
    '140' => ['139', 'right' ],
    '150' => ['149', 'right' ],
    '160' => ['159', 'right' ],
    '170' => ['169', 'right' ],
    '180' => ['179', 'right' ],
    '190' => ['189', 'right' ],
    '200' => ['199', 'right' ],
    '201' => ['199', 'right', 'right' ],
    '202' => ['199', 'right', 'right', 'right' ],
    '203' => ['199', 'right', 'right', 'right', 'right' ],
    '204' => ['199', 'right', 'right', 'right', 'right', 'right' ],
    '205' => ['199', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '206' => ['211', 'left', 'left', 'left', 'left', 'left' ],
    '207' => ['211', 'left', 'left', 'left', 'left' ],
    '208' => ['211', 'left', 'left', 'left' ],
    '209' => ['211', 'left', 'left' ],
    '210' => ['211', 'left' ],
    '220' => ['219', 'right' ],
    '230' => ['229', 'right' ],
    '240' => ['239', 'right' ],
    '250' => ['249', 'right' ],
    '260' => ['259', 'right' ],
    '270' => ['269', 'right' ],
    '280' => ['279', 'right' ],
    '290' => ['289', 'right' ],
    '300' => ['299', 'right' ],
    '301' => ['299', 'right', 'right' ],
    '302' => ['299', 'right', 'right', 'right' ],
    '303' => ['299', 'right', 'right', 'right', 'right' ],
    '304' => ['299', 'right', 'right', 'right', 'right', 'right' ],
    '305' => ['299', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '306' => ['311', 'left', 'left', 'left', 'left', 'left' ],
    '307' => ['311', 'left', 'left', 'left', 'left' ],
    '308' => ['311', 'left', 'left', 'left' ],
    '309' => ['311', 'left', 'left' ],
    '310' => ['311', 'left' ],
    '320' => ['319', 'right' ],
    '330' => ['329', 'right' ],
    '340' => ['339', 'right' ],
    '350' => ['349', 'right' ],
    '360' => ['359', 'right' ],
    '370' => ['369', 'right' ],
    '380' => ['379', 'right' ],
    '390' => ['389', 'right' ],
    '400' => ['399', 'right' ],
    '401' => ['399', 'right', 'right' ],
    '402' => ['399', 'right', 'right', 'right' ],
    '403' => ['399', 'right', 'right', 'right', 'right' ],
    '404' => ['399', 'right', 'right', 'right', 'right', 'right' ],
    '405' => ['399', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '406' => ['411', 'left', 'left', 'left', 'left', 'left' ],
    '407' => ['411', 'left', 'left', 'left', 'left' ],
    '408' => ['411', 'left', 'left', 'left' ],
    '409' => ['411', 'left', 'left' ],
    '410' => ['411', 'left' ],
    '420' => ['419', 'right' ],
    '430' => ['429', 'right' ],
    '440' => ['439', 'right' ],
    '450' => ['449', 'right' ],
    '460' => ['459', 'right' ],
    '470' => ['469', 'right' ],
    '480' => ['479', 'right' ],
    '490' => ['489', 'right' ],
    '500' => ['499', 'right' ],
    '501' => ['499', 'right', 'right' ],
    '502' => ['499', 'right', 'right', 'right' ],
    '503' => ['499', 'right', 'right', 'right', 'right' ],
    '504' => ['499', 'right', 'right', 'right', 'right', 'right' ],
    '505' => ['499', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '506' => ['511', 'left', 'left', 'left', 'left', 'left' ],
    '507' => ['511', 'left', 'left', 'left', 'left' ],
    '508' => ['511', 'left', 'left', 'left' ],
    '509' => ['511', 'left', 'left' ],
    '510' => ['511', 'left' ],
    '520' => ['519', 'right' ],
    '530' => ['529', 'right' ],
    '540' => ['539', 'right' ],
    '550' => ['551', 'left' ], # 549 is HBO OnDemand for me
    '560' => ['559', 'right' ],
    '570' => ['569', 'right' ],
    '580' => ['579', 'right' ],
    '590' => ['589', 'right' ],
    '600' => ['599', 'right' ],
    '601' => ['599', 'right', 'right' ],
    '602' => ['599', 'right', 'right', 'right' ],
    '603' => ['599', 'right', 'right', 'right', 'right' ],
    '604' => ['599', 'right', 'right', 'right', 'right', 'right' ],
    '605' => ['599', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '606' => ['611', 'left', 'left', 'left', 'left', 'left' ],
    '607' => ['611', 'left', 'left', 'left', 'left' ],
    '608' => ['611', 'left', 'left', 'left' ],
    '609' => ['611', 'left', 'left' ],
    '610' => ['611', 'left' ],
    '620' => ['619', 'right' ],
    '630' => ['629', 'right' ],
    '640' => ['639', 'right' ],
    '650' => ['649', 'right' ],
    '660' => ['659', 'right' ],
    '670' => ['669', 'right' ],
    '680' => ['679', 'right' ],
    '690' => ['689', 'right' ],
    '700' => ['699', 'right' ],
    '701' => ['699', 'right', 'right' ],
    '702' => ['699', 'right', 'right', 'right' ],
    '703' => ['699', 'right', 'right', 'right', 'right' ],
    '704' => ['699', 'right', 'right', 'right', 'right', 'right' ],
    '705' => ['699', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '706' => ['711', 'left', 'left', 'left', 'left', 'left' ],
    '707' => ['711', 'left', 'left', 'left', 'left' ],
    '708' => ['711', 'left', 'left', 'left' ],
    '709' => ['711', 'left', 'left' ],
    '710' => ['711', 'left' ],
    '720' => ['719', 'right' ],
    '730' => ['729', 'right' ],
    '740' => ['739', 'right' ],
    '750' => ['749', 'right' ],
    '760' => ['759', 'right' ],
    '770' => ['769', 'right' ],
    '780' => ['779', 'right' ],
    '790' => ['789', 'right' ],
    '800' => ['799', 'right' ],
    '801' => ['799', 'right', 'right' ],
    '802' => ['799', 'right', 'right', 'right' ],
    '803' => ['799', 'right', 'right', 'right', 'right' ],
    '804' => ['799', 'right', 'right', 'right', 'right', 'right' ],
    '805' => ['799', 'right', 'right', 'right', 'right', 'right', 'right' ],
    '806' => ['811', 'left', 'left', 'left', 'left', 'left' ],
    '807' => ['811', 'left', 'left', 'left', 'left' ],
    '808' => ['811', 'left', 'left', 'left' ],
    '809' => ['811', 'left', 'left' ],
    '810' => ['811', 'left' ],
    '820' => ['819', 'right' ],
    '830' => ['829', 'right' ],
    '840' => ['839', 'right' ],
    '850' => ['849', 'right' ],
    '860' => ['859', 'right' ],
    '870' => ['869', 'right' ],
    '880' => ['879', 'right' ],
    '900' => ['911', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left' ],
    '901' => ['911', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left' ],
    '902' => ['911', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left' ],
    '903' => ['911', 'left', 'left', 'left', 'left', 'left', 'left', 'left', 'left' ],
    '904' => ['911', 'left', 'left', 'left', 'left', 'left', 'left', 'left' ],
    '905' => ['911', 'left', 'left', 'left', 'left', 'left', 'left' ],
    '906' => ['911', 'left', 'left', 'left', 'left', 'left' ],
    '907' => ['911', 'left', 'left', 'left', 'left' ],
    '908' => ['911', 'left', 'left', 'left' ],
    '909' => ['911', 'left', 'left' ],
    '910' => ['911', 'left' ],
    '920' => ['919', 'right' ],
    '930' => ['929', 'right' ],
    '940' => ['939', 'right' ],
    '950' => ['949', 'right' ],
    '960' => ['959', 'right' ],
    '970' => ['969', 'right' ],
    '980' => ['979', 'right' ],
    '990' => ['989', 'right' ]);
}

```

 I started messing with the bottom code and realized it would be easier to mess with the top portion. I didn't require the zero padding so I removed it.

 And then I went into MythBuntu setup, went to my capture card, svideo input, and entered /usr/bin/change_channel.pl in the external change channel script field.

 And it works! 

 Oh, don't forget to sudo chmod 755 /usr/bin/change_channel.pl

 Enjoy!

---

