---
title: "snmpget problems  with custom MIB on Hardy"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by sanat on 2009-11-15
Hi,

I am running snmp & snmpd 5.4.1~dfsg-4ubuntu4.3 on Hardy.

I made this small MIB - TEST-CASE-MIB.txt and placed it in $HOME/.snmp/mibs, and also added the line *mibs +TEST-CASE-MIB* to $HOME/.snmp/snmp.conf. (for rwcommunity, community string is *readwrite*). 

snmptranslate works but snmpget says- no object available (and snmpwalk does not return anything). What could be going wrong? :( Am I missing something? :(. 

$snmptranslate   .1.3.6.1.4.1.30000
TEST-CASE-MIB::testcaseModule

$snmpget -v2c -c readwrite 10.64.22.124 .1.3.6.1.4.1.30000.1
**TEST-CASE-MIB::testcaseGroup = No Such Object available on this agent at this OID**


TEST-CASE-MIB.txt
-----------------


	TEST-CASE-MIB DEFINITIONS ::= BEGIN

 

		IMPORTS

			OBJECT-GROUP			

				FROM SNMPv2-CONF			

			enterprises, Integer32, OBJECT-TYPE, MODULE-IDENTITY			

				FROM SNMPv2-SMI;

	

	

		-- 1.3.6.1.4.1.30000

		testcaseModule MODULE-IDENTITY 

			LAST-UPDATED "200911151908Z"		-- November 15, 2009 at 19:08 GMT

			ORGANIZATION 

				"Organization."

			CONTACT-INFO 

				"Contact-info."

			DESCRIPTION 

				"Description."

			::= { enterprises 30000 }



		

	

--

-- Node definitions

--

	

		-- 1.3.6.1.4.1.30000.1

		testcaseGroup OBJECT-GROUP

			OBJECTS { testcaseNode1, testcaseNode2 }

			STATUS current

			DESCRIPTION 

				"Description."

			::= { testcaseModule 1 }



		

		-- 1.3.6.1.4.1.30000.2

		testcaseObjid OBJECT IDENTIFIER ::= { testcaseModule 2 }



		

		-- 1.3.6.1.4.1.30000.2.1

		testcaseNode1 OBJECT-TYPE

			SYNTAX Integer32

			MAX-ACCESS read-write

			STATUS current

			DESCRIPTION

				"Description."

			::= { testcaseObjid 1 }



		

		-- 1.3.6.1.4.1.30000.2.2

		testcaseNode2 OBJECT-TYPE

			SYNTAX Integer32

			MAX-ACCESS read-write

			STATUS current

			DESCRIPTION

				"Description."

			::= { testcaseObjid 2 }



		

	

	END

---

### Post by sanat on 2009-11-15
Sorry, forgot to mention...it returns the same in following cases too-

$snmpget -v2c -c readwrite 10.64.22.124 .1.3.6.1.4.1.30000.2.1
TEST-CASE-MIB::testcaseNode1 = No Such Object available on this agent at this OID
$ snmpget -v2c -c readwrite 10.64.22.124 .1.3.6.1.4.1.30000.2.2
TEST-CASE-MIB::testcaseNode2 = No Such Object available on this agent at this OID
snmpget -v2c -c readwrite 10.64.22.124 .1.3.6.1.4.1.30000.2.2.0
TEST-CASE-MIB::testcaseNode2.0 = No Such Object available on this agent at this OID
$ snmpget -v2c -c readwrite 10.64.22.124 .1.3.6.1.4.1.30000.2.1.0
TEST-CASE-MIB::testcaseNode1.0 = No Such Object available on this agent at this OID

---

