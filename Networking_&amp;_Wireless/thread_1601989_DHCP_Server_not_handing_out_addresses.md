---
title: "DHCP Server not handing out addresses"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by stayrollin on 2010-10-20
I have a MacBook Pro running VirtualBox with Ubuntu 10.10 as a guest. I am trying to run a DHCP server from within the Ubuntu VM. I need to do this in order to run a multicast utility. On a stand alone machine running Fedcora I have this working without fail but within the Ubuntu VM I am having troubles. The DHCP server is starting okay, but when I use a cross over cable connected to a device the device does not ever get an address.

I have eth1 bound to my ethernet jack where I am trying to source the addresses, and eth2 bound to my airport which is disabled unless I need internet access.

Here is my DHCP.conf file
```

###############################################################################
# Amino Communications Sample dhcpd.conf file                                 #
#                                                                             #
# Note, this is not a complete dhcpd.conf file.  It just covers the various   #
# settings required for Amino AmiNet STB multicast bootstraping               #
# it may require some changes for deployment on your network.                 #
#                                                                             #
# 29.01.04 - Created Paul Rae                                                 #
# 20.08.04 - Aminet500 and Aminet110H added by Richard Warren                 #
# 03.10.05 - AMINO.local-config added by Steve McIntyre                       #
# 29.03.06 - Aminet124 and mboot bootrom versions added by Rob Thornburrow    #
#                                                                             #
###############################################################################

###############################################################################
# Misc dhcp options                                                           #
###############################################################################
        allow bootp;
        ddns-update-style ad-hoc;
        filename="AMINET.txt";



###############################################################################
# Extra Options for AMINO option space (used for multicast)                   #
###############################################################################
        option space AMINO;
        option AMINO.address             code  1 = ip-address;
        option AMINO.port                code  2 = integer 16;
        option AMINO.product             code  3 = text;
        option AMINO.option              code  4 = text;
        option AMINO.version             code  5 = text;
        option AMINO.middleware          code  6 = ip-address;
        option AMINO.mw_port             code  7 = integer 16;
        option AMINO.homepage            code  8 = text;
        option AMINO.dindex              code  9 = integer 32;
        option AMINO.dindex_min          code 10 = integer 32;
        option AMINO.dindex_page         code 11 = text;
        option AMINO.STBrc-mcast-address code 12 = ip-address;
        option AMINO.STBrc-mcast-port    code 13 = integer 16;
        option AMINO.STBrc-unicast-port  code 14 = integer 16;
        option AMINO.local-config        code 15 = text;
        option AMINO.timezone            code 16 = text;
        option AMINO.middleware2         code 17 = ip-address;
        option AMINO.mw_args             code 18 = text;
        option AMINO.test_host           code 19 = ip-address;
        option AMINO.test_dir            code 20 = text;
        option AMINO.recovery_mode       code 21 = integer 8;
        option AMINO.mirimon_args        code 22 = text;

###############################################################################
# AmiNET103 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET103 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET103 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET103 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.50.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET103 mboot"                                                     #
# AmiNET103 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET103 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET103mboot<bootrom version>") or
           ((substring( option vendor-encapsulated-options, 2, 9)="AMINET103")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.50;
  option AMINO.port 11111;
}
###############################################################################

###############################################################################
# Class "AmiNET103 upgrd"                                                     #
# AmiNET103 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET103 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet103upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet103")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.51;
  option AMINO.port 11111;
}
###############################################################################

###############################################################################
# Class "AmiNET103 fisys"                                                     #
# AmiNET103 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET103 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet103fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet103")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}





###############################################################################
# AmiNET110 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET110 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET110 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET110 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.50.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET110 mboot"                                                     #
# AmiNET110 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET110 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET11xmboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET11x")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET110 upgrd"                                                     #
# AmiNET110 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET110 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet110upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet110")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET110 fisys"                                                     #
# AmiNET110 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET110 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet110fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet110")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}




###############################################################################
# AmiNET110H Configuration Section                                            #
###############################################################################
#                                                                             #
# class "AmiNET110H mboot" - boot state when requesting bootstrap image       #
# class "AmiNET110H upgrd" - boot state when requesting main upgrade image    #
# class "AmiNET110H fisys" - boot state when in normal state                  #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.50.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET110H mboot"                                                    #
# AmiNET110H - response to bootrom request for a bootstrap image              #
###############################################################################
class "AmiNET110H mboot"
{
  match if (option vendor-class-identifier="aminoAMINET110Hmboot<bootrom version>") or
          ((substring(option vendor-encapsulated-options, 2, 10)="AMINET110H")
           and (substring(option vendor-encapsulated-options, 14, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET110H upgrd"                                                    #
# AmiNET110H - response to bootstrap request for a main upgrade image         #
###############################################################################
class "AmiNET110H upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet110hupgrd") or
           ((substring( option vendor-encapsulated-options,2,10)="aminet110h")
            and (substring( option vendor-encapsulated-options,14,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET110h fisys"                                                    #
# AmiNET110 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET110H fisys"
{
  match if (option vendor-class-identifier="Aminoaminet110hfisys") or
          ((substring( option vendor-encapsulated-options, 2, 10)="aminet110h")
           and (substring(option vendor-encapsulated-options, 14, 5)="fisys"));

  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}




###############################################################################
# AmiNET500 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET500 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET500 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET500 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.50.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET500 mboot"                                                     #
# AmiNET500 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET500 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET5xxmboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET5xx")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET500 upgrd"                                                     #
# AmiNET500 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET500 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet500upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet500")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET500 fisys"                                                     #
# AmiNET500 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET500 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet500fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet500")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}




###############################################################################
# AmiNET124 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET124 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET124 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET124 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.50.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET124 mboot"                                                     #
# AmiNET124 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET124 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET124mboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET124")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET124 upgrd"                                                     #
# AmiNET124 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET124 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet124upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet124")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.50.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET124 fisys"                                                     #
# AmiNET124 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET124 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet124fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet124")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}



###############################################################################
# AmiNET125 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET125 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET125 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET125 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.50.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET125 mboot"                                                     #
# AmiNET125 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET125 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET125mboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET125")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  # option AMINO.address <mcast address>;
  # option AMINO.port <port>;
}

###############################################################################
# Class "AmiNET125 upgrd"                                                     #
# AmiNET125 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET125 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet125upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet125")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  # option AMINO.address <mcast address>;
  # option AMINO.port <port>;
}

###############################################################################
# Class "AmiNET125 fisys"                                                     #
# AmiNET125 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET125 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet125fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet125")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}




###############################################################################
# Class "AmiNET120 mboot"                                                     #
# AmiNET120 - response when bootstrapping                                     #
###############################################################################
class "AMINET120 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET120mboot") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET120")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

#  option log-servers	10.172.2.20;
  vendor-option-space AMINO;
  option AMINO.address 239.255.224.100;
  option AMINO.port 1001;
}

###############################################################################
# Class "AmiNET120 upgrd"                                                     #
# AmiNET120 - response when upgrading                                         #
###############################################################################
class "aminet120 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet120upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet120")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 239.255.224.101;
  option AMINO.port 1001;
}




###############################################################################
# AmiNET130 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET130 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET130 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET130 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.51.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET130 mboot"                                                     #
# AmiNET130 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET130 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET130mboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET130")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.51.50;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET130 upgrd"                                                     #
# AmiNET130 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET130 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet130upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet130")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.51.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET130 fisys"                                                     #
# AmiNET130 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET130 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet130fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet130")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}



###############################################################################
# AmiNET130H Configuration Section                                            #
###############################################################################
#                                                                             #
# class "AmiNET130H mboot" - boot state when requesting bootstrap image       #
# class "AmiNET130H upgrd" - boot state when requesting main upgrade image    #
# class "AmiNET130H fisys" - boot state when in normal state                  #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.52.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET130H mboot"                                                    #
# AmiNET130H - response to bootrom request for a bootstrap image              #
###############################################################################
class "AmiNET130H mboot"
{
  match if (option vendor-class-identifier="aminoAMINET130Hmboot<bootrom version>") or
          ((substring(option vendor-encapsulated-options, 2, 10)="AMINET130H")
           and (substring(option vendor-encapsulated-options, 14, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.51.51;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET130H upgrd"                                                    #
# AmiNET130H - response to bootstrap request for a main upgrade image         #
###############################################################################
class "AmiNET130H upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet130hupgrd") or
           ((substring( option vendor-encapsulated-options,2,10)="aminet130h")
            and (substring( option vendor-encapsulated-options,14,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.51.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET130h fisys"                                                    #
# AmiNET130 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET130H fisys"
{
  match if (option vendor-class-identifier="Aminoaminet130hfisys") or
          ((substring( option vendor-encapsulated-options, 2, 10)="aminet130h")
           and (substring(option vendor-encapsulated-options, 14, 5)="fisys"));

  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}





###############################################################################
# AmiNET131 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET131 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET131 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET131 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.53.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET131 mboot"                                                     #
# AmiNET131 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET131 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET131mboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET131")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.53.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET131 upgrd"                                                     #
# AmiNET131 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET131 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet131upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet131")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.53.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET131 fisys"                                                     #
# AmiNET131 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET131 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet131fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet131")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}





###############################################################################
# AmiNET530 Configuration Section                                             #
###############################################################################
#                                                                             #
# class "AmiNET530 mboot" - boot state when requesting bootstrap image        #
# class "AmiNET530 upgrd" - boot state when requesting main upgrade image     #
# class "AmiNET530 fisys" - boot state when in normal state                   #
#                                                                             #
# The only items that may need changing are as follows:                       #
#                                                                             #
# option AMINO.address 225.50.54.50; - the multicast address you are          #
# streaming on                                                                #
# option AMINO.port 11111; - the port you are streaming on                    #
#                                                                             #
# If you change any of these options you must also make sure you make the     #
# appropriate changes to /etc/mcastbootd.conf                                 #
#                                                                             #
# In the mboot class, the bootrom version (e.g. 1.32) must be given in the    #
# vendor-class-identifier.  If multiple bootrom versions need to be supported #
# multiple match cases may be used.                                           #
#                                                                             #
###############################################################################



###############################################################################
# Class "AmiNET530 mboot"                                                     #
# AmiNET530 - response to bootrom request for a bootstrap image               #
###############################################################################
class "AmiNET530 mboot"
{
  match if (option vendor-class-identifier="aminoAMINET530mboot<bootrom version>") or
           (option vendor-class-identifier="insecureAMINET530mboot<bootrom version>") or
           ((substring(option vendor-encapsulated-options, 2, 9)="AMINET530")
            and (substring(option vendor-encapsulated-options, 13, 5)="mboot"));                                                                                
  vendor-option-space AMINO;
  option AMINO.address 225.50.54.52;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET530 upgrd"                                                     #
# AmiNET530 - response to bootstrap request for a main upgrade image          #
###############################################################################
class "AmiNET530 upgrd"
{
  match if (option vendor-class-identifier="Aminoaminet530upgrd") or
           ((substring( option vendor-encapsulated-options,2,9)="aminet530")
            and (substring( option vendor-encapsulated-options,13,5)="upgrd"));

  vendor-option-space AMINO;
  option AMINO.address 225.50.54.53;
  option AMINO.port 11111;
}

###############################################################################
# Class "AmiNET530 fisys"                                                     #
# AmiNET530 - response when booting in normal boot state                      #
###############################################################################
class "AmiNET530 fisys"
{
  match if (option vendor-class-identifier="Aminoaminet530fisys") or
           ((substring( option vendor-encapsulated-options, 2, 9)="aminet530")
            and (substring(option vendor-encapsulated-options, 13, 5)="fisys"));
  vendor-option-space AMINO;
  # option AMINO.middleware <mcast address>;
  # option AMINO.mw_port <port>;
}



###############################################################################
# Subnet Declaration                                                          #
###############################################################################
subnet 192.168.1.0 netmask 255.255.255.0 {

###############################################################################
# Default Gateway - This MUST be set!!                                        #
###############################################################################
option routers 192.168.1.1;

###############################################################################
# Subnet Mask - This MUST be set!!                                            #
###############################################################################
option subnet-mask 255.255.255.0;

###############################################################################
# Domain Name - Optional                                                      #
###############################################################################
option domain-name "blahblah.com";

###############################################################################
# DNS Servers  - Optional                                                     #
###############################################################################
option domain-name-servers 192.168.1.1,192.168.1.2;

###############################################################################
# Time Offset - Optional                                                      #
###############################################################################
option time-offset -5; # Eastern Standard Time

###############################################################################
# Address Pool - This MUST be set!!                                           #
#                                                                             #
# In this address pool we list the classes which we wish to give addresses to,#
# unless a device is in this list it will not be given a address!             #
#                                                                             #
###############################################################################
pool {
        range dynamic-bootp 192.168.1.50 192.168.1.100;
        range 192.168.1.101 192.168.1.200;

        # AmiNET103 Member Classes
        #allow members of "AmiNET103 mboot";
        #allow members of "AmiNET103 upgrd";
        #allow members of "AmiNET103 fisys";

        # AmiNET110 Member Classes
        #allow members of "AmiNET110 mboot";
        #allow members of "AmiNET110 upgrd";
        #allow members of "AmiNET110 fisys";
     }

}




###############################################################################
# End dhcpd.conf                                                              #
###############################################################################

```

tail syslog
```

Oct 20 20:41:44 ubuntu rtkit-daemon[1127]: Successfully made thread 1259 of process 1259 (n/a) owned by '1000' high priority at nice level -11.
Oct 20 20:41:44 ubuntu rtkit-daemon[1127]: Supervising 4 threads of 2 processes of 1 users.
Oct 20 20:41:44 ubuntu pulseaudio[1259]: pid.c: Daemon already running.
Oct 20 20:41:44 ubuntu pulseaudio[1118]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Oct 20 20:41:44 ubuntu pulseaudio[1118]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Oct 20 20:41:44 ubuntu pulseaudio[1118]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Oct 20 20:41:44 ubuntu kernel: [   33.955721] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Oct 20 20:41:47 ubuntu init: plymouth-stop pre-start process (1371) terminated with status 1
Oct 20 20:42:25 ubuntu ntpdate[1317]: can't find host ntp.ubuntu.com
Oct 20 20:42:25 ubuntu ntpdate[1317]: no servers can be used, exiting

```

and ifconfig
```

eth1      Link encap:Ethernet  HWaddr 08:00:27:89:ab:2e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe89:ab2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20730 (20.7 KB)  TX bytes:33403 (33.4 KB)

eth2      Link encap:Ethernet  HWaddr 08:00:27:23:fe:6f  
          inet6 addr: fe80::a00:27ff:fe23:fe6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3031 (3.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21837 (21.8 KB)  TX bytes:21837 (21.8 KB)

```

---

### Post by relay_man on 2010-10-21
I'm wondering: :confused:


>  when I use a [COLOR="Red"]cross over cable[/COLOR] connected to a device the device does not ever get an address.

What other "device" are you connecting to, and have you tried a straight cable instead of a crossover cable?

---

### Post by stayrollin on 2010-10-21
The devices are set top boxes. I haven't tried a straight through. I am not using a hub or switch between the computer and STB so I would think I would need a cross over.

---

### Post by Iowan on 2010-10-21
Some gigabit cards can auto-configure - so the might be able to use a straight cable... but they should handle a crossover as well :confused:

---

