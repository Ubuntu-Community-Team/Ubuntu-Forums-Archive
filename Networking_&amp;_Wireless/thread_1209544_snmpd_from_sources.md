---
title: "snmpd from sources"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by francesco.spegni on 2009-07-10
hi there,

following the guides:

[http://blog.zenoss.com/2009/02/18/tip-of-the-month-snmp-software-inventory-for-debian-and-ubuntu-machines/](http://blog.zenoss.com/2009/02/18/tip-of-the-month-snmp-software-inventory-for-debian-and-ubuntu-machines/)

and

[http://www.howtoforge.com/how-to-rebuild-the-squid-2.6-debian-package-with-support-for-x-forwarded-for-headers](http://www.howtoforge.com/how-to-rebuild-the-squid-2.6-debian-package-with-support-for-x-forwarded-for-headers)

i was trying to rebuild the snmpd package including the --enable-embedded-perl flag in the configure step. after having download the package sources with:

sudo apt-get source snmpd

and its dependencies with:

sudo apt-get build-dep snmpd

i executed ./configure with no error and the 

debuild -uc -us -b

obtaining the following error message:

libtool: link: cc -shared  .libs/snmp_client.o .libs/mib.o .libs/parse.o .libs/snmp_api.o .libs/snmp.o .libs/snmp_auth.o .libs/asn1.o .libs/md5.o .libs/snmp_parse_args.o .libs/system.o .libs/vacm.o .libs/int64.o .libs/read_config.o .libs/pkcs.o .libs/snmp_debug.o .libs/tools.o .libs/snmp_logging.o .libs/text_utils.o .libs/snmpv3.o .libs/lcd_time.o .libs/keytools.o .libs/file_utils.o .libs/scapi.o .libs/callback.o .libs/default_store.o .libs/snmp_alarm.o .libs/data_list.o .libs/oid_stash.o .libs/fd_event_manager.o .libs/mt_support.o .libs/snmp_enum.o .libs/snmp-tc.o .libs/snmp_service.o .libs/snprintf.o .libs/strlcpy.o .libs/strtol.o .libs/strtoul.o .libs/strtok_r.o .libs/snmp_transport.o .libs/snmpUDPIPv6Domain.o .libs/snmpTCPIPv6Domain.o .libs/snmpUDPDomain.o .libs/snmpTCPDomain.o .libs/snmpUnixDomain.o .libs/snmpCallbackDomain.o .libs/snmp_secmod.o .libs/snmpusm.o .libs/snmp_version.o .libs/check_varbind.o .libs/container.o .libs/container_binary_array.o .libs/container_null.o .libs/container_list_ssll.o .libs/container_iterator.o .libs/cmu_compat.o .libs/ucd_compat.o   -lcrypto  -Wl,-Bsymbolic-functions   -Wl,-soname -Wl,libnetsnmp.so.15 -o .libs/libnetsnmp.so.15.1.0
cc: .libs/snmpUDPIPv6Domain.o: No such file or directory
cc: .libs/snmpTCPIPv6Domain.o: No such file or directory
make[2]: *** [libnetsnmp.la] Error 1
make[2]: Leaving directory `/etc/snmp/net-snmp-5.4.1~dfsg/snmplib'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/etc/snmp/net-snmp-5.4.1~dfsg'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

(long version attached). did i forget to install something? is there a way to fix it? 

thanks in advance :)

---

### Post by jonobr on 2009-07-10
Hello

Im not sure about the error but what are you trying to accomplish?

Whats the end game on this?

Ive worked with snmp for certain applications I may be able to suggest something.

---

### Post by Carlos Santiago on 2009-08-24
Hi Jonobr,
I don't know what Francesco want to do, but maybe is something similar to what I need. I want to make an SNMP agent the answers to snmp sets and snmp gets.
I have already defined the MIB for the agent. Now I want to:
1) Parse the mib to C, C++ or Java
2) Write the agent
3) Improve the agent to perform some actions (for example after setting some value)

I am trying to make it with:
1) mib2c
2) snmpd

I found some tutorial sites (like [http://www.net-snmp.org/wiki/index.php/TUT:Writing_a_MIB_Module](http://www.net-snmp.org/wiki/index.php/TUT:Writing_a_MIB_Module)).
However, they require the usage of snmpd sources, and I am having some problems compiling them. (Like Francesco seems to be having).

Could you advise me on how can I make my agent? 

If I need to install the snmpd sources, is this enough?
sudo apt-get source snmpd
sudo apt-get build-dep snmpd

Is it possible to circumvent the requirement of the sources?
I want to do it in Ubuntu 8.04.

I would be very appreciated for some help.

Thank you.

---

### Post by jonobr on 2009-08-25
Hello


Im not sure I can answer your question.

If I understand you correctly, it sounds as if you have some implementation of SNMP to do the query but you want to implement and agent to go on a targeted device and as you said, respond to the gets and sets from the issuer.

If so, Im pretty sure I cant help.
snmp and snmpd in synaptic are on the server side and would not be for the agent.

Im not sure how you would go about building an agent.
I have seen solutions whereby management of devices that dont support snmp can be implemented between a SNMP utility and the element to translate snmp queries to commands the device supports, i.e. maybe ssh or telnet to a device and retrieve info, but they were highly customised solution/


Sorry I cant be of much help:(

---

