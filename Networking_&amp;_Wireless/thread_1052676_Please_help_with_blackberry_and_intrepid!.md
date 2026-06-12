---
title: "Please help with blackberry and intrepid!"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by snwagner on 2009-01-28
I have done everything it seems!  I've followed every forum post and to no avail...  I've attempted to follow every step...  
This is just one of the forums I attempted to follow:
[http://ubuntuforums.org/showthread.php?p=3838257](http://ubuntuforums.org/showthread.php?p=3838257)
I'm a total newbie to linux and ubuntu, I really would like help with this.  The blackberry is a 7130 through alltel (though I don't think that matters).  :popcorn:
This is what I get when trying to go through the first step (install Xlt)
```
sean@laptop:~/Desktop/Xlt-13.0.13$ make
make  all-recursive
make[1]: Entering directory `/home/sean/Desktop/Xlt-13.0.13'
Making all in .
make[2]: Entering directory `/home/sean/Desktop/Xlt-13.0.13'
make[2]: Leaving directory `/home/sean/Desktop/Xlt-13.0.13'
Making all in lib
make[2]: Entering directory `/home/sean/Desktop/Xlt-13.0.13/lib'
/bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -Inone      -g -O2 -Wall -c -o NumEntry.lo `test -f 'NumEntry.c' || echo './'`NumEntry.c
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -Inone -g -O2 -Wall -c NumEntry.c  -fPIC -DPIC -o .libs/NumEntry.o
NumEntry.c:33:22: error: Xm/TextF.h: No such file or directory
NumEntry.c:34:22: error: Xm/Label.h: No such file or directory
NumEntry.c:35:23: error: Xm/ArrowB.h: No such file or directory
NumEntry.c:36:26: error: Xm/RowColumn.h: No such file or directory
NumEntry.c:37:25: error: Xm/MessageB.h: No such file or directory
In file included from NumEntry.c:38:
./NumEntryP.h:28:22: error: Xm/FormP.h: No such file or directory
In file included from NumEntry.c:38:
./NumEntryP.h:43: error: expected specifier-qualifier-list before 'XmString'
./NumEntryP.h:54: error: expected specifier-qualifier-list before 'XmManagerPart'
./NumEntryP.h:68: error: expected specifier-qualifier-list before 'XmManagerClassPart'
NumEntry.c:73: error: 'XmNlabelString' undeclared here (not in a function)
NumEntry.c:73: error: 'XmCLabelString' undeclared here (not in a function)
NumEntry.c:73: error: 'XmRXmString' undeclared here (not in a function)
NumEntry.c:74: error: 'XmString' undeclared here (not in a function)
NumEntry.c:74: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:75: error: 'XmRImmediate' undeclared here (not in a function)
NumEntry.c:78: error: 'XmNvalue' undeclared here (not in a function)
NumEntry.c:78: error: 'XmCValue' undeclared here (not in a function)
NumEntry.c:78: error: 'XtRString' undeclared here (not in a function)
NumEntry.c:79: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:83: error: 'XmNcolumns' undeclared here (not in a function)
NumEntry.c:83: error: 'XmCColumns' undeclared here (not in a function)
NumEntry.c:83: error: 'XmRShort' undeclared here (not in a function)
NumEntry.c:84: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:85: error: 'XtRImmediate' undeclared here (not in a function)
NumEntry.c:88: error: 'XmNvalueChangedCallback' undeclared here (not in a function)
NumEntry.c:88: error: 'XtCCallback' undeclared here (not in a function)
NumEntry.c:88: error: 'XtRCallback' undeclared here (not in a function)
NumEntry.c:89: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:93: error: 'XmNactivateCallback' undeclared here (not in a function)
NumEntry.c:94: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:98: error: 'XmNlosingFocusCallback' undeclared here (not in a function)
NumEntry.c:99: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:103: error: 'XmNhelpCallback' undeclared here (not in a function)
NumEntry.c:104: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:108: error: 'XtRInt' undeclared here (not in a function)
NumEntry.c:109: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:114: error: 'XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:122: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'syn_resources'
NumEntry.c:180: error: 'xmFormClassRec' undeclared here (not in a function)
NumEntry.c:180: error: initializer element is not constant
NumEntry.c:180: error: (near initialization for 'xrwsNumEntryClassRec.core_class.superclass')
NumEntry.c:225: error: 'XmFormConstraintRec' undeclared here (not in a function)
NumEntry.c:225: error: initializer element is not constant
NumEntry.c:225: error: (near initialization for 'xrwsNumEntryClassRec.constraint_class.constraint_size')
NumEntry.c:232: error: extra brace group at end of initializer
NumEntry.c:232: error: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:233: error: 'XmInheritTranslations' undeclared here (not in a function)
NumEntry.c:234: error: 'syn_resources' undeclared here (not in a function)
NumEntry.c:235: error: invalid operands to binary / (have 'struct XtResource *' and 'unsigned int')
NumEntry.c:238: error: 'XmInheritParentProcess' undeclared here (not in a function)
NumEntry.c:240: warning: excess elements in struct initializer
NumEntry.c:240: warning: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:242: error: extra brace group at end of initializer
NumEntry.c:242: error: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:245: error: 'XmInheritFocusMovedProc' undeclared here (not in a function)
NumEntry.c:247: warning: excess elements in struct initializer
NumEntry.c:247: warning: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:249: error: extra brace group at end of initializer
NumEntry.c:249: error: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:251: warning: excess elements in struct initializer
NumEntry.c:251: warning: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:253: error: extra brace group at end of initializer
NumEntry.c:253: error: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c:255: warning: excess elements in struct initializer
NumEntry.c:255: warning: (near initialization for 'xrwsNumEntryClassRec')
NumEntry.c: In function '_AutoRepeat':
NumEntry.c:278: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:278: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:279: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:279: error: request for member 'Delay' in something not a structure or union
NumEntry.c:281: warning: passing argument 2 of 'XtAppAddTimeOut' makes integer from pointer without a cast
NumEntry.c:281: warning: statement with no effect
NumEntry.c:282: warning: passing argument 2 of 'XtCallCallbacks' from incompatible pointer type
NumEntry.c:286: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:286: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:286: warning: statement with no effect
NumEntry.c: In function 'AutoRepeat':
NumEntry.c:299: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:299: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:301: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:301: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:302: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:302: error: request for member 'InitialDelay' in something not a structure or union
NumEntry.c:304: warning: passing argument 2 of 'XtAppAddTimeOut' makes integer from pointer without a cast
NumEntry.c:304: warning: statement with no effect
NumEntry.c:309: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:309: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:311: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:311: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:311: warning: passing argument 1 of 'XtRemoveTimeOut' makes integer from pointer without a cast
NumEntry.c:312: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:312: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:312: warning: statement with no effect
NumEntry.c: In function 'DoMath':
NumEntry.c:327: warning: implicit declaration of function 'XmTextFieldGetString'
NumEntry.c:327: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:327: error: request for member 'TextField' in something not a structure or union
NumEntry.c:327: warning: assignment makes pointer from integer without a cast
NumEntry.c:328: warning: implicit declaration of function 'XmTextFieldGetInsertionPosition'
NumEntry.c:328: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:328: error: request for member 'TextField' in something not a structure or union
NumEntry.c:330: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:330: error: request for member 'result' in something not a structure or union
NumEntry.c:330: error: invalid operands to binary != (have 'double' and 'struct XtResource *')
NumEntry.c:335: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:335: error: request for member 'result' in something not a structure or union
NumEntry.c:335: warning: statement with no effect
NumEntry.c:336: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:336: error: request for member 'columns' in something not a structure or union
NumEntry.c:336: warning: field precision should have type 'int', but argument 3 has type 'struct XtResource *'
NumEntry.c:337: error: 'XmCR_VALUE_CHANGED' undeclared (first use in this function)
NumEntry.c:337: error: (Each undeclared identifier is reported only once
NumEntry.c:337: error: for each function it appears in.)
NumEntry.c:337: warning: assignment makes integer from pointer without a cast
NumEntry.c:341: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:341: error: request for member 'result' in something not a structure or union
NumEntry.c:341: error: incompatible types in assignment
NumEntry.c:341: warning: statement with no effect
NumEntry.c:342: warning: passing argument 2 of 'XtCallCallbacks' from incompatible pointer type
NumEntry.c:345: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:345: error: request for member 'value' in something not a structure or union
NumEntry.c:345: warning: passing argument 1 of 'XtFree' from incompatible pointer type
NumEntry.c:346: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:346: error: request for member 'value' in something not a structure or union
NumEntry.c:346: warning: statement with no effect
NumEntry.c:347: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:347: error: request for member 'result' in something not a structure or union
NumEntry.c:347: warning: statement with no effect
NumEntry.c:354: warning: implicit declaration of function 'XmTextFieldSetString'
NumEntry.c:354: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:354: error: request for member 'TextField' in something not a structure or union
NumEntry.c:354: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:354: error: request for member 'value' in something not a structure or union
NumEntry.c:355: warning: implicit declaration of function 'XmTextFieldSetInsertionPosition'
NumEntry.c:355: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:355: error: request for member 'TextField' in something not a structure or union
NumEntry.c: In function 'LosingFocus':
NumEntry.c:369: warning: passing argument 2 of 'XtCallCallbacks' from incompatible pointer type
NumEntry.c: In function 'Activate':
NumEntry.c:381: warning: passing argument 2 of 'XtCallCallbacks' from incompatible pointer type
NumEntry.c: In function 'StepValue':
NumEntry.c:481: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:481: error: request for member 'TextField' in something not a structure or union
NumEntry.c:481: warning: assignment makes pointer from integer without a cast
NumEntry.c:482: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:482: error: request for member 'TextField' in something not a structure or union
NumEntry.c:486: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:486: error: request for member 'TextField' in something not a structure or union
NumEntry.c:487: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:487: error: request for member 'TextField' in something not a structure or union
NumEntry.c: In function 'destroy':
NumEntry.c:505: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:505: error: request for member 'value' in something not a structure or union
NumEntry.c:505: warning: passing argument 1 of 'XtFree' from incompatible pointer type
NumEntry.c: In function 'initialize':
NumEntry.c:516: warning: implicit declaration of function 'XtHeight'
NumEntry.c:516: error: lvalue required as left operand of assignment
NumEntry.c:516: warning: statement with no effect
NumEntry.c:517: warning: implicit declaration of function 'XtWidth'
NumEntry.c:517: error: lvalue required as left operand of assignment
NumEntry.c:517: warning: statement with no effect
NumEntry.c:518: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:518: error: request for member 'value' in something not a structure or union
NumEntry.c:518: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:518: error: request for member 'value' in something not a structure or union
NumEntry.c:518: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:518: error: request for member 'value' in something not a structure or union
NumEntry.c:518: warning: passing argument 1 of 'strlen' from incompatible pointer type
NumEntry.c:518: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:518: error: request for member 'value' in something not a structure or union
NumEntry.c:518: warning: passing argument 2 of 'strcpy' from incompatible pointer type
NumEntry.c:518: warning: statement with no effect
NumEntry.c:519: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:519: error: request for member 'Label' in something not a structure or union
NumEntry.c:519: warning: implicit declaration of function 'XmCreateLabel'
NumEntry.c:519: warning: statement with no effect
NumEntry.c:520: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:520: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:522: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:522: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:522: warning: implicit declaration of function 'XmStringCreateSimple'
NumEntry.c:522: warning: statement with no effect
NumEntry.c:524: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:524: error: request for member 'Label' in something not a structure or union
NumEntry.c:525: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:525: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:526: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:527: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:527: error: request for member 'Label' in something not a structure or union
NumEntry.c:527: warning: passing argument 1 of 'XtOverrideTranslations' from incompatible pointer type
NumEntry.c:528: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:528: error: request for member 'Label' in something not a structure or union
NumEntry.c:528: warning: passing argument 1 of 'XtManageChild' from incompatible pointer type
NumEntry.c:529: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:529: error: request for member 'Label' in something not a structure or union
NumEntry.c:529: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:529: error: request for member 'Label' in something not a structure or union
NumEntry.c:529: error: lvalue required as left operand of assignment
NumEntry.c:529: warning: statement with no effect
NumEntry.c:530: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:530: error: request for member 'Label' in something not a structure or union
NumEntry.c:530: error: lvalue required as left operand of assignment
NumEntry.c:530: warning: statement with no effect
NumEntry.c:532: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:532: error: request for member 'TextField' in something not a structure or union
NumEntry.c:532: warning: implicit declaration of function 'XmCreateTextField'
NumEntry.c:532: warning: statement with no effect
NumEntry.c:533: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:533: error: request for member 'TextField' in something not a structure or union
NumEntry.c:533: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:533: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:534: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:534: error: request for member 'TextField' in something not a structure or union
NumEntry.c:534: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:534: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:535: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:535: error: request for member 'TextField' in something not a structure or union
NumEntry.c:535: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:535: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:536: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:536: error: request for member 'TextField' in something not a structure or union
NumEntry.c:537: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:537: error: request for member 'value' in something not a structure or union
NumEntry.c:538: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:538: error: request for member 'columns' in something not a structure or union
NumEntry.c:539: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:540: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:540: error: request for member 'TextField' in something not a structure or union
NumEntry.c:540: warning: passing argument 1 of 'XtOverrideTranslations' from incompatible pointer type
NumEntry.c:541: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:541: error: request for member 'TextField' in something not a structure or union
NumEntry.c:541: warning: passing argument 1 of 'XtOverrideTranslations' from incompatible pointer type
NumEntry.c:542: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:542: error: request for member 'TextField' in something not a structure or union
NumEntry.c:542: warning: passing argument 1 of 'XtManageChild' from incompatible pointer type
NumEntry.c:543: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:543: error: request for member 'TextField' in something not a structure or union
NumEntry.c:543: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:543: error: request for member 'TextField' in something not a structure or union
NumEntry.c:543: error: lvalue required as left operand of assignment
NumEntry.c:543: warning: statement with no effect
NumEntry.c:544: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:544: error: request for member 'TextField' in something not a structure or union
NumEntry.c:544: error: lvalue required as left operand of assignment
NumEntry.c:544: warning: statement with no effect
NumEntry.c:547: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:547: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:547: warning: implicit declaration of function 'XmCreateRowColumn'
NumEntry.c:547: warning: statement with no effect
NumEntry.c:548: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:548: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:549: error: 'XmNtraversalOn' undeclared (first use in this function)
NumEntry.c:550: error: 'XmNpacking' undeclared (first use in this function)
NumEntry.c:550: error: 'XmPACK_COLUMN' undeclared (first use in this function)
NumEntry.c:551: error: 'XmNorientation' undeclared (first use in this function)
NumEntry.c:551: error: 'XmHORIZONTAL' undeclared (first use in this function)
NumEntry.c:552: error: 'XmNnumColumns' undeclared (first use in this function)
NumEntry.c:553: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:554: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:554: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:554: warning: passing argument 1 of 'XtOverrideTranslations' from incompatible pointer type
NumEntry.c:555: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:555: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:555: warning: implicit declaration of function 'XmCreateArrowButton'
NumEntry.c:555: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:555: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:555: warning: statement with no effect
NumEntry.c:556: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:556: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:556: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:556: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:557: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:557: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:557: error: 'XmNarmCallback' undeclared (first use in this function)
NumEntry.c:557: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:557: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:558: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:558: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:558: error: 'XmNdisarmCallback' undeclared (first use in this function)
NumEntry.c:558: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:558: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:559: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:559: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:560: error: 'XmNwidth' undeclared (first use in this function)
NumEntry.c:561: error: 'XmNarrowDirection' undeclared (first use in this function)
NumEntry.c:561: error: 'XmARROW_UP' undeclared (first use in this function)
NumEntry.c:562: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:563: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:563: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:563: warning: passing argument 1 of 'XtOverrideTranslations' from incompatible pointer type
NumEntry.c:564: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:564: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:564: warning: passing argument 1 of 'XtManageChild' from incompatible pointer type
NumEntry.c:565: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:565: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:565: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:565: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:565: warning: statement with no effect
NumEntry.c:566: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:566: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:566: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:566: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:567: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:567: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:567: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:567: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:568: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:568: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:568: warning: passing argument 1 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:568: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:569: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:569: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:571: error: 'XmARROW_DOWN' undeclared (first use in this function)
NumEntry.c:572: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:573: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:573: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:573: warning: passing argument 1 of 'XtOverrideTranslations' from incompatible pointer type
NumEntry.c:574: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:574: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:574: warning: passing argument 1 of 'XtManageChild' from incompatible pointer type
NumEntry.c:575: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:575: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:576: error: 'XmNtopAttachment' undeclared (first use in this function)
NumEntry.c:576: error: 'XmATTACH_FORM' undeclared (first use in this function)
NumEntry.c:577: error: 'XmNbottomAttachment' undeclared (first use in this function)
NumEntry.c:578: error: 'XmNleftAttachment' undeclared (first use in this function)
NumEntry.c:578: error: 'XmATTACH_NONE' undeclared (first use in this function)
NumEntry.c:579: error: 'XmNrightAttachment' undeclared (first use in this function)
NumEntry.c:580: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:581: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:581: error: request for member 'TextField' in something not a structure or union
NumEntry.c:585: error: 'XmATTACH_WIDGET' undeclared (first use in this function)
NumEntry.c:586: error: 'XmNrightWidget' undeclared (first use in this function)
NumEntry.c:586: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:586: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:587: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:588: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:588: error: request for member 'Label' in something not a structure or union
NumEntry.c:589: error: 'XmNalignment' undeclared (first use in this function)
NumEntry.c:589: error: 'XmALIGNMENT_BEGINNING' undeclared (first use in this function)
NumEntry.c:594: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:594: error: request for member 'TextField' in something not a structure or union
NumEntry.c:595: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:599: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:599: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:599: warning: passing argument 1 of 'XtQueryGeometry' from incompatible pointer type
NumEntry.c:600: error: lvalue required as left operand of assignment
NumEntry.c:600: warning: statement with no effect
NumEntry.c:602: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:602: error: request for member 'RowColumn' in something not a structure or union
NumEntry.c:602: warning: passing argument 1 of 'XtManageChild' from incompatible pointer type
NumEntry.c:603: warning: passing argument 2 of 'XtAddCallback' from incompatible pointer type
NumEntry.c:604: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:604: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:604: warning: statement with no effect
NumEntry.c:605: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:605: error: request for member 'result' in something not a structure or union
NumEntry.c:605: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:605: error: request for member 'value' in something not a structure or union
NumEntry.c:605: warning: passing argument 1 of 'XltCalc' from incompatible pointer type
NumEntry.c:605: warning: statement with no effect
NumEntry.c: In function 'set_values':
NumEntry.c:618: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:618: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:620: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:620: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:620: warning: passing argument 1 of 'XtRemoveTimeOut' makes integer from pointer without a cast
NumEntry.c:621: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:621: error: request for member 'TimerId' in something not a structure or union
NumEntry.c:621: warning: statement with no effect
NumEntry.c:624: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:624: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:624: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:624: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:626: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:626: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:626: warning: implicit declaration of function 'XmStringCopy'
NumEntry.c:626: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:626: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:626: warning: statement with no effect
NumEntry.c:627: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:627: error: request for member 'Label' in something not a structure or union
NumEntry.c:628: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:628: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:629: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:630: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:630: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:632: warning: implicit declaration of function 'XmStringFree'
NumEntry.c:632: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:632: error: request for member 'LabelString' in something not a structure or union
NumEntry.c:635: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:635: error: request for member 'value' in something not a structure or union
NumEntry.c:635: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:635: error: request for member 'value' in something not a structure or union
NumEntry.c:643: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:643: error: request for member 'value' in something not a structure or union
NumEntry.c:643: warning: assignment from incompatible pointer type
NumEntry.c:644: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:644: error: request for member 'value' in something not a structure or union
NumEntry.c:644: warning: statement with no effect
NumEntry.c:645: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:645: error: request for member 'TextField' in something not a structure or union
NumEntry.c:646: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:646: error: request for member 'TextField' in something not a structure or union
NumEntry.c:646: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:646: error: request for member 'value' in something not a structure or union
NumEntry.c:647: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:647: error: request for member 'TextField' in something not a structure or union
NumEntry.c:648: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:648: error: request for member 'value' in something not a structure or union
NumEntry.c:650: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:650: error: request for member 'value' in something not a structure or union
NumEntry.c:650: warning: passing argument 1 of 'XtFree' from incompatible pointer type
NumEntry.c:655: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:655: error: request for member 'columns' in something not a structure or union
NumEntry.c:655: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:655: error: request for member 'columns' in something not a structure or union
NumEntry.c:657: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:657: error: request for member 'TextField' in something not a structure or union
NumEntry.c:659: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:659: error: request for member 'TextField' in something not a structure or union
NumEntry.c:660: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:660: error: request for member 'columns' in something not a structure or union
NumEntry.c:661: warning: passing argument 1 of 'XtVaSetValues' from incompatible pointer type
NumEntry.c:662: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:662: error: request for member 'TextField' in something not a structure or union
NumEntry.c:662: error: lvalue required as left operand of assignment
NumEntry.c:662: warning: statement with no effect
NumEntry.c: In function 'NEGetValue':
NumEntry.c:675: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:675: error: request for member 'TextField' in something not a structure or union
NumEntry.c: In function 'NEGetColumns':
NumEntry.c:684: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:684: error: request for member 'TextField' in something not a structure or union
NumEntry.c:686: warning: passing argument 1 of 'XtVaGetValues' from incompatible pointer type
NumEntry.c: In function 'KeyPad':
NumEntry.c:701: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:701: error: request for member 'TextField' in something not a structure or union
NumEntry.c:701: warning: passing argument 1 of 'XtCallActionProc' from incompatible pointer type
NumEntry.c: In function 'Up':
NumEntry.c:712: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:712: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:712: warning: passing argument 1 of 'XtCallActionProc' from incompatible pointer type
NumEntry.c: In function 'Down':
NumEntry.c:723: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:723: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:723: warning: passing argument 1 of 'XtCallActionProc' from incompatible pointer type
NumEntry.c: In function 'Help':
NumEntry.c:759: warning: statement with no effect
NumEntry.c:759: error: expected ';' before 'string'
NumEntry.c:762: error: 'applicationShellWidgetClass' undeclared (first use in this function)
NumEntry.c:762: error: 'topLevelShellWidgetClass' undeclared (first use in this function)
NumEntry.c:764: warning: implicit declaration of function 'XmCreateInformationDialog'
NumEntry.c:764: warning: assignment makes pointer from integer without a cast
NumEntry.c:765: error: 'string' undeclared (first use in this function)
NumEntry.c:765: warning: implicit declaration of function 'XmStringCreateLtoR'
NumEntry.c:765: error: 'XmFONTLIST_DEFAULT_TAG' undeclared (first use in this function)
NumEntry.c:765: warning: statement with no effect
NumEntry.c:767: error: 'XmNmessageString' undeclared (first use in this function)
NumEntry.c: In function 'XltVaCreateNumEntry':
NumEntry.c:795: warning: missing sentinel in function call
NumEntry.c: In function 'XltNumEntryGetChild':
NumEntry.c:808: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:808: error: request for member 'TextField' in something not a structure or union
NumEntry.c:808: warning: return from incompatible pointer type
NumEntry.c:811: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:811: error: request for member 'Label' in something not a structure or union
NumEntry.c:811: warning: return from incompatible pointer type
NumEntry.c:814: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:814: error: request for member 'UpArrow' in something not a structure or union
NumEntry.c:814: warning: return from incompatible pointer type
NumEntry.c:817: error: 'struct _XltNumEntryRec' has no member named 'num_entry'
NumEntry.c:817: error: request for member 'DnArrow' in something not a structure or union
NumEntry.c:817: warning: return from incompatible pointer type
make[2]: *** [NumEntry.lo] Error 1
make[2]: Leaving directory `/home/sean/Desktop/Xlt-13.0.13/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sean/Desktop/Xlt-13.0.13'
make: *** [all] Error 2

```

---

### Post by snwagner on 2009-01-28
Bump..
Really trying to get help tonight

---

### Post by snwagner on 2009-01-28
bump again

---

### Post by kevdog on 2009-01-28
Hold on -- its taking me a while to download and compile packages!

I think you need openmotif installed first before xlt -- but lets see. I'm trying now!

---

### Post by kevdog on 2009-01-28
Need to catch you tomorrow -- I'm currently compiling OpenMotif from CVS on my old junker and its taking awhile.  I can tell you however that OpenMotif needs to be compiled and installed prior to installing libXlt.

---

### Post by snwagner on 2009-01-28
Patiently waiting thanks so much

---

### Post by snwagner on 2009-01-28
I suppose that will work...  Will wait to hear that will try openmotif but i have already and same types of errorss

---

### Post by snwagner on 2009-01-28
Ok...
Here's the results for ./configure on openmotif:
```
sean@laptop:~/Desktop$ cd open*
sean@laptop:~/Desktop/openmotif-2.3.0$ ./configure
checking for /usr/X/include/X11/X.h... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... f77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for f77 option to produce PIC... -fPIC
checking if f77 PIC flag -fPIC works... yes
checking if f77 static flag -static works... yes
checking if f77 supports -c -o file.o... yes
checking whether the f77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... /usr/bin/f77: Illegal option: -print-search-dirs
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for byacc... byacc
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether libXt was compiled with -DXTHREADS... yes
checking X11/Xos_r.h usability... yes
checking X11/Xos_r.h presence... yes
checking for X11/Xos_r.h... yes
checking X11/Xpoll.h usability... yes
checking X11/Xpoll.h presence... yes
checking for X11/Xpoll.h... yes
checking X11/Xmu/Editres.h usability... no
checking X11/Xmu/Editres.h presence... yes
configure: WARNING: X11/Xmu/Editres.h: present but cannot be compiled
configure: WARNING: X11/Xmu/Editres.h:     check for missing prerequisite headers?
configure: WARNING: X11/Xmu/Editres.h: see the Autoconf documentation
configure: WARNING: X11/Xmu/Editres.h:     section "Present But Cannot Be Compiled"
configure: WARNING: X11/Xmu/Editres.h: proceeding with the preprocessor's result
configure: WARNING: X11/Xmu/Editres.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for X11/Xmu/Editres.h... yes
checking for _XEditResCheckMessages in -lXmu... yes
checking for XmuNCopyISOLatin1Lowered  in -lXmu... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking sys/malloc.h usability... no
checking sys/malloc.h presence... no
checking for sys/malloc.h... no
checking for strings.h... (cached) yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking wctype.h usability... yes
checking wctype.h presence... yes
checking for wctype.h... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for X11/Xos_r.h... (cached) yes
checking for X11/Xpoll.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uid_t in sys/types.h... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for working memcmp... yes
checking whether setpgrp takes no argument... yes
checking return type of signal handlers... void
checking for working strcoll... yes
checking for strftime... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for vprintf... yes
checking for _doprnt... no
checking whether sprintf returns void... yes
checking for wcslen... yes
checking for wcscpy... yes
checking for wcsncpy... yes
checking for wcschr... yes
checking for wcscat... yes
checking for wcsncat... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for mkdir... yes
checking for re_comp... yes
checking for regcmp... no
checking for select... yes
checking for strcspn... yes
checking for strerror... yes
checking for strstr... yes
checking for strtod... yes
checking for strtol... yes
checking for uname... yes
checking for strdup... yes
checking for strcasecmp... yes
checking for putenv... yes
checking for regcomp... yes
checking for memmove... yes
checking for iconv_open in -liconv... no
checking for freetype-config... freetype-config
checking freetype/freetype.h usability... no
checking freetype/freetype.h presence... no
checking for freetype/freetype.h... no
checking X11/extensions/Xrender.h usability... no
checking X11/extensions/Xrender.h presence... no
checking for X11/extensions/Xrender.h... no
checking for fontconfig-config... no
checking fontconfig/fontconfig.h usability... yes
checking fontconfig/fontconfig.h presence... yes
checking for fontconfig/fontconfig.h... yes
checking for FcInit... no
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for jpeg_start_decompress... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_create_read_struct... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bitmaps/Makefile
config.status: creating clients/Makefile
config.status: creating clients/mwm/Makefile
config.status: creating clients/mwm/WmWsmLib/Makefile
config.status: creating clients/uil/Makefile
config.status: creating clients/xmbind/Makefile
config.status: creating config/Makefile
config.status: creating config/cf/Makefile
config.status: creating config/imake/Makefile
config.status: creating config/util/Makefile
config.status: creating config/makedepend/Makefile
config.status: creating include/Makefile
config.status: creating include/Dt/Makefile
config.status: creating lib/Makefile
config.status: creating lib/Xm/Makefile
config.status: creating lib/Mrm/Makefile
config.status: creating localized/Makefile
config.status: creating localized/util/Makefile
config.status: creating doc/Makefile
config.status: creating doc/man/Makefile
config.status: creating doc/man/man1/Makefile
config.status: creating doc/man/man3/Makefile
config.status: creating doc/man/man4/Makefile
config.status: creating doc/man/man5/Makefile
config.status: creating tools/Makefile
config.status: creating tools/wml/Makefile
config.status: creating demos/Makefile
config.status: creating demos/lib/Makefile
config.status: creating demos/lib/Xmd/Makefile
config.status: creating demos/lib/Wsm/Makefile
config.status: creating demos/lib/Exm/Makefile
config.status: creating demos/lib/Exm/wml/Makefile
config.status: creating demos/programs/Makefile
config.status: creating demos/programs/Exm/Makefile
config.status: creating demos/programs/Exm/app_in_c/Makefile
config.status: creating demos/programs/Exm/app_in_uil/Makefile
config.status: creating demos/programs/Exm/simple_app/Makefile
config.status: creating demos/programs/airport/Makefile
config.status: creating demos/programs/animate/Makefile
config.status: creating demos/programs/drag_and_drop/Makefile
config.status: creating demos/programs/draw/Makefile
config.status: creating demos/programs/earth/Makefile
config.status: creating demos/programs/filemanager/Makefile
config.status: creating demos/programs/fileview/Makefile
config.status: creating demos/programs/getsubres/Makefile
config.status: creating demos/programs/hellomotif/Makefile
config.status: creating demos/programs/hellomotifi18n/Makefile
config.status: creating demos/programs/hellomotifi18n/C/Makefile
config.status: creating demos/programs/hellomotifi18n/C/uid/Makefile
config.status: creating demos/programs/hellomotifi18n/english/Makefile
config.status: creating demos/programs/hellomotifi18n/english/uid/Makefile
config.status: creating demos/programs/hellomotifi18n/french/Makefile
config.status: creating demos/programs/hellomotifi18n/french/uid/Makefile
config.status: creating demos/programs/hellomotifi18n/hebrew/Makefile
config.status: creating demos/programs/hellomotifi18n/hebrew/uid/Makefile
config.status: creating demos/programs/hellomotifi18n/japan/Makefile
config.status: creating demos/programs/hellomotifi18n/japan/uid/Makefile
config.status: creating demos/programs/hellomotifi18n/japanese/Makefile
config.status: creating demos/programs/hellomotifi18n/japanese/uid/Makefile
config.status: creating demos/programs/hellomotifi18n/swedish/Makefile
config.status: creating demos/programs/hellomotifi18n/swedish/uid/Makefile
config.status: creating demos/programs/i18ninput/Makefile
config.status: creating demos/programs/panner/Makefile
config.status: creating demos/programs/periodic/Makefile
config.status: creating demos/programs/piano/Makefile
config.status: creating demos/programs/popups/Makefile
config.status: creating demos/programs/sampler2_0/Makefile
config.status: creating demos/programs/setdate/Makefile
config.status: creating demos/programs/todo/Makefile
config.status: creating demos/programs/workspace/Makefile
config.status: creating demos/programs/tooltips/Makefile
config.status: creating demos/programs/FontSel/Makefile
config.status: creating demos/programs/ButtonBox/Makefile
config.status: creating demos/programs/ColorSel/Makefile
config.status: creating demos/programs/Column/Makefile
config.status: creating demos/programs/Combo2/Makefile
config.status: creating demos/programs/Ext18List/Makefile
config.status: creating demos/programs/Ext18List/pixmaps/Makefile
config.status: creating demos/programs/IconB/Makefile
config.status: creating demos/programs/Outline/Makefile
config.status: creating demos/programs/Paned/Makefile
config.status: creating demos/programs/TabStack/Makefile
config.status: creating demos/programs/Tree/Makefile
config.status: creating demos/programs/pixmaps/Makefile
config.status: creating demos/unsupported/Makefile
config.status: creating demos/unsupported/Exm/Makefile
config.status: creating demos/unsupported/aicon/Makefile
config.status: creating demos/unsupported/dainput/Makefile
config.status: creating demos/unsupported/dogs/Makefile
config.status: creating demos/unsupported/hellomotif/Makefile
config.status: creating demos/unsupported/motifshell/Makefile
config.status: creating demos/unsupported/uilsymdump/Makefile
config.status: creating demos/unsupported/xmapdef/Makefile
config.status: creating demos/unsupported/xmfonts/Makefile
config.status: creating demos/unsupported/xmforc/Makefile
config.status: creating demos/unsupported/xmform/Makefile
config.status: creating demos/doc/Makefile
config.status: creating demos/doc/programGuide/Makefile
config.status: creating demos/doc/programGuide/ch05/Makefile
config.status: creating demos/doc/programGuide/ch05/Scale/Makefile
config.status: creating demos/doc/programGuide/ch06/Makefile
config.status: creating demos/doc/programGuide/ch06/spin_box/Makefile
config.status: creating demos/doc/programGuide/ch06/combo_box/Makefile
config.status: creating demos/doc/programGuide/ch08/Makefile
config.status: creating demos/doc/programGuide/ch08/Notebook/Makefile
config.status: creating demos/doc/programGuide/ch08/Container/Makefile
config.status: creating demos/doc/programGuide/ch16/Makefile
config.status: creating demos/doc/programGuide/ch17/Makefile
config.status: creating demos/doc/programGuide/ch17/simple_drop/Makefile
config.status: creating demos/doc/programGuide/ch17/simple_drag/Makefile
config.status: creating lib/Xm/xmstring.list
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating lib/Xm/Xm.h
config.status: lib/Xm/Xm.h is unchanged
config.status: executing depfiles commands
sean@laptop:~/Desktop/openmotif-2.3.0$ 


```
but you'll notice that halfway through I get this error
```

checking for X11/Xos_r.h... yes
checking X11/Xpoll.h usability... yes
checking X11/Xpoll.h presence... yes
checking for X11/Xpoll.h... yes
checking X11/Xmu/Editres.h usability... no
checking X11/Xmu/Editres.h presence... yes
configure: WARNING: X11/Xmu/Editres.h: present but cannot be compiled
configure: WARNING: X11/Xmu/Editres.h:     check for missing prerequisite headers?
configure: WARNING: X11/Xmu/Editres.h: see the Autoconf documentation
configure: WARNING: X11/Xmu/Editres.h:     section "Present But Cannot Be Compiled"
configure: WARNING: X11/Xmu/Editres.h: proceeding with the preprocessor's result
configure: WARNING: X11/Xmu/Editres.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for X11/Xmu/Editres.h... yes
```

See...  I cannot install openmotif either.  :(](*,)

P.S.  I'm using Ubuntu 8.1

---

### Post by snwagner on 2009-01-28
Ok.. Here's what I get for openmotif when I do make.
```
	then mv -f ".deps/Command.Tpo" ".deps/Command.Plo"; else rm -f ".deps/Command.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Command.lo -MD -MP -MF .deps/Command.Tpo -c Command.c  -fPIC -DPIC -o .libs/Command.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Command.lo -MD -MP -MF .deps/Command.Tpo -c Command.c -o Command.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT CutPaste.lo -MD -MP -MF ".deps/CutPaste.Tpo" -c -o CutPaste.lo CutPaste.c; \
	then mv -f ".deps/CutPaste.Tpo" ".deps/CutPaste.Plo"; else rm -f ".deps/CutPaste.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT CutPaste.lo -MD -MP -MF .deps/CutPaste.Tpo -c CutPaste.c  -fPIC -DPIC -o .libs/CutPaste.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT CutPaste.lo -MD -MP -MF .deps/CutPaste.Tpo -c CutPaste.c -o CutPaste.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT Dest.lo -MD -MP -MF ".deps/Dest.Tpo" -c -o Dest.lo Dest.c; \
	then mv -f ".deps/Dest.Tpo" ".deps/Dest.Plo"; else rm -f ".deps/Dest.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Dest.lo -MD -MP -MF .deps/Dest.Tpo -c Dest.c  -fPIC -DPIC -o .libs/Dest.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Dest.lo -MD -MP -MF .deps/Dest.Tpo -c Dest.c -o Dest.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DialogS.lo -MD -MP -MF ".deps/DialogS.Tpo" -c -o DialogS.lo DialogS.c; \
	then mv -f ".deps/DialogS.Tpo" ".deps/DialogS.Plo"; else rm -f ".deps/DialogS.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DialogS.lo -MD -MP -MF .deps/DialogS.Tpo -c DialogS.c  -fPIC -DPIC -o .libs/DialogS.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DialogS.lo -MD -MP -MF .deps/DialogS.Tpo -c DialogS.c -o DialogS.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DialogSE.lo -MD -MP -MF ".deps/DialogSE.Tpo" -c -o DialogSE.lo DialogSE.c; \
	then mv -f ".deps/DialogSE.Tpo" ".deps/DialogSE.Plo"; else rm -f ".deps/DialogSE.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DialogSE.lo -MD -MP -MF .deps/DialogSE.Tpo -c DialogSE.c  -fPIC -DPIC -o .libs/DialogSE.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DialogSE.lo -MD -MP -MF .deps/DialogSE.Tpo -c DialogSE.c -o DialogSE.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DragBS.lo -MD -MP -MF ".deps/DragBS.Tpo" -c -o DragBS.lo DragBS.c; \
	then mv -f ".deps/DragBS.Tpo" ".deps/DragBS.Plo"; else rm -f ".deps/DragBS.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragBS.lo -MD -MP -MF .deps/DragBS.Tpo -c DragBS.c  -fPIC -DPIC -o .libs/DragBS.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragBS.lo -MD -MP -MF .deps/DragBS.Tpo -c DragBS.c -o DragBS.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DragC.lo -MD -MP -MF ".deps/DragC.Tpo" -c -o DragC.lo DragC.c; \
	then mv -f ".deps/DragC.Tpo" ".deps/DragC.Plo"; else rm -f ".deps/DragC.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragC.lo -MD -MP -MF .deps/DragC.Tpo -c DragC.c  -fPIC -DPIC -o .libs/DragC.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragC.lo -MD -MP -MF .deps/DragC.Tpo -c DragC.c -o DragC.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DragOverS.lo -MD -MP -MF ".deps/DragOverS.Tpo" -c -o DragOverS.lo DragOverS.c; \
	then mv -f ".deps/DragOverS.Tpo" ".deps/DragOverS.Plo"; else rm -f ".deps/DragOverS.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragOverS.lo -MD -MP -MF .deps/DragOverS.Tpo -c DragOverS.c  -fPIC -DPIC -o .libs/DragOverS.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragOverS.lo -MD -MP -MF .deps/DragOverS.Tpo -c DragOverS.c -o DragOverS.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DragICC.lo -MD -MP -MF ".deps/DragICC.Tpo" -c -o DragICC.lo DragICC.c; \
	then mv -f ".deps/DragICC.Tpo" ".deps/DragICC.Plo"; else rm -f ".deps/DragICC.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragICC.lo -MD -MP -MF .deps/DragICC.Tpo -c DragICC.c  -fPIC -DPIC -o .libs/DragICC.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragICC.lo -MD -MP -MF .deps/DragICC.Tpo -c DragICC.c -o DragICC.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DragIcon.lo -MD -MP -MF ".deps/DragIcon.Tpo" -c -o DragIcon.lo DragIcon.c; \
	then mv -f ".deps/DragIcon.Tpo" ".deps/DragIcon.Plo"; else rm -f ".deps/DragIcon.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragIcon.lo -MD -MP -MF .deps/DragIcon.Tpo -c DragIcon.c  -fPIC -DPIC -o .libs/DragIcon.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragIcon.lo -MD -MP -MF .deps/DragIcon.Tpo -c DragIcon.c -o DragIcon.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DragUnder.lo -MD -MP -MF ".deps/DragUnder.Tpo" -c -o DragUnder.lo DragUnder.c; \
	then mv -f ".deps/DragUnder.Tpo" ".deps/DragUnder.Plo"; else rm -f ".deps/DragUnder.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragUnder.lo -MD -MP -MF .deps/DragUnder.Tpo -c DragUnder.c  -fPIC -DPIC -o .libs/DragUnder.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DragUnder.lo -MD -MP -MF .deps/DragUnder.Tpo -c DragUnder.c -o DragUnder.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DrawingA.lo -MD -MP -MF ".deps/DrawingA.Tpo" -c -o DrawingA.lo DrawingA.c; \
	then mv -f ".deps/DrawingA.Tpo" ".deps/DrawingA.Plo"; else rm -f ".deps/DrawingA.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DrawingA.lo -MD -MP -MF .deps/DrawingA.Tpo -c DrawingA.c  -fPIC -DPIC -o .libs/DrawingA.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DrawingA.lo -MD -MP -MF .deps/DrawingA.Tpo -c DrawingA.c -o DrawingA.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DrawnB.lo -MD -MP -MF ".deps/DrawnB.Tpo" -c -o DrawnB.lo DrawnB.c; \
	then mv -f ".deps/DrawnB.Tpo" ".deps/DrawnB.Plo"; else rm -f ".deps/DrawnB.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DrawnB.lo -MD -MP -MF .deps/DrawnB.Tpo -c DrawnB.c  -fPIC -DPIC -o .libs/DrawnB.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DrawnB.lo -MD -MP -MF .deps/DrawnB.Tpo -c DrawnB.c -o DrawnB.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DropSMgr.lo -MD -MP -MF ".deps/DropSMgr.Tpo" -c -o DropSMgr.lo DropSMgr.c; \
	then mv -f ".deps/DropSMgr.Tpo" ".deps/DropSMgr.Plo"; else rm -f ".deps/DropSMgr.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DropSMgr.lo -MD -MP -MF .deps/DropSMgr.Tpo -c DropSMgr.c  -fPIC -DPIC -o .libs/DropSMgr.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DropSMgr.lo -MD -MP -MF .deps/DropSMgr.Tpo -c DropSMgr.c -o DropSMgr.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DropSMgrI.lo -MD -MP -MF ".deps/DropSMgrI.Tpo" -c -o DropSMgrI.lo DropSMgrI.c; \
	then mv -f ".deps/DropSMgrI.Tpo" ".deps/DropSMgrI.Plo"; else rm -f ".deps/DropSMgrI.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DropSMgrI.lo -MD -MP -MF .deps/DropSMgrI.Tpo -c DropSMgrI.c  -fPIC -DPIC -o .libs/DropSMgrI.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DropSMgrI.lo -MD -MP -MF .deps/DropSMgrI.Tpo -c DropSMgrI.c -o DropSMgrI.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT DropTrans.lo -MD -MP -MF ".deps/DropTrans.Tpo" -c -o DropTrans.lo DropTrans.c; \
	then mv -f ".deps/DropTrans.Tpo" ".deps/DropTrans.Plo"; else rm -f ".deps/DropTrans.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DropTrans.lo -MD -MP -MF .deps/DropTrans.Tpo -c DropTrans.c  -fPIC -DPIC -o .libs/DropTrans.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT DropTrans.lo -MD -MP -MF .deps/DropTrans.Tpo -c DropTrans.c -o DropTrans.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT ExtObject.lo -MD -MP -MF ".deps/ExtObject.Tpo" -c -o ExtObject.lo ExtObject.c; \
	then mv -f ".deps/ExtObject.Tpo" ".deps/ExtObject.Plo"; else rm -f ".deps/ExtObject.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT ExtObject.lo -MD -MP -MF .deps/ExtObject.Tpo -c ExtObject.c  -fPIC -DPIC -o .libs/ExtObject.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT ExtObject.lo -MD -MP -MF .deps/ExtObject.Tpo -c ExtObject.c -o ExtObject.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT FileSB.lo -MD -MP -MF ".deps/FileSB.Tpo" -c -o FileSB.lo FileSB.c; \
	then mv -f ".deps/FileSB.Tpo" ".deps/FileSB.Plo"; else rm -f ".deps/FileSB.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT FileSB.lo -MD -MP -MF .deps/FileSB.Tpo -c FileSB.c  -fPIC -DPIC -o .libs/FileSB.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT FileSB.lo -MD -MP -MF .deps/FileSB.Tpo -c FileSB.c -o FileSB.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT Form.lo -MD -MP -MF ".deps/Form.Tpo" -c -o Form.lo Form.c; \
	then mv -f ".deps/Form.Tpo" ".deps/Form.Plo"; else rm -f ".deps/Form.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Form.lo -MD -MP -MF .deps/Form.Tpo -c Form.c  -fPIC -DPIC -o .libs/Form.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Form.lo -MD -MP -MF .deps/Form.Tpo -c Form.c -o Form.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT Frame.lo -MD -MP -MF ".deps/Frame.Tpo" -c -o Frame.lo Frame.c; \
	then mv -f ".deps/Frame.Tpo" ".deps/Frame.Plo"; else rm -f ".deps/Frame.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Frame.lo -MD -MP -MF .deps/Frame.Tpo -c Frame.c  -fPIC -DPIC -o .libs/Frame.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Frame.lo -MD -MP -MF .deps/Frame.Tpo -c Frame.c -o Frame.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT Gadget.lo -MD -MP -MF ".deps/Gadget.Tpo" -c -o Gadget.lo Gadget.c; \
	then mv -f ".deps/Gadget.Tpo" ".deps/Gadget.Plo"; else rm -f ".deps/Gadget.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Gadget.lo -MD -MP -MF .deps/Gadget.Tpo -c Gadget.c  -fPIC -DPIC -o .libs/Gadget.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Gadget.lo -MD -MP -MF .deps/Gadget.Tpo -c Gadget.c -o Gadget.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT GadgetUtil.lo -MD -MP -MF ".deps/GadgetUtil.Tpo" -c -o GadgetUtil.lo GadgetUtil.c; \
	then mv -f ".deps/GadgetUtil.Tpo" ".deps/GadgetUtil.Plo"; else rm -f ".deps/GadgetUtil.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT GadgetUtil.lo -MD -MP -MF .deps/GadgetUtil.Tpo -c GadgetUtil.c  -fPIC -DPIC -o .libs/GadgetUtil.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT GadgetUtil.lo -MD -MP -MF .deps/GadgetUtil.Tpo -c GadgetUtil.c -o GadgetUtil.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT GeoUtils.lo -MD -MP -MF ".deps/GeoUtils.Tpo" -c -o GeoUtils.lo GeoUtils.c; \
	then mv -f ".deps/GeoUtils.Tpo" ".deps/GeoUtils.Plo"; else rm -f ".deps/GeoUtils.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT GeoUtils.lo -MD -MP -MF .deps/GeoUtils.Tpo -c GeoUtils.c  -fPIC -DPIC -o .libs/GeoUtils.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT GeoUtils.lo -MD -MP -MF .deps/GeoUtils.Tpo -c GeoUtils.c -o GeoUtils.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT ImageCache.lo -MD -MP -MF ".deps/ImageCache.Tpo" -c -o ImageCache.lo ImageCache.c; \
	then mv -f ".deps/ImageCache.Tpo" ".deps/ImageCache.Plo"; else rm -f ".deps/ImageCache.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT ImageCache.lo -MD -MP -MF .deps/ImageCache.Tpo -c ImageCache.c  -fPIC -DPIC -o .libs/ImageCache.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT ImageCache.lo -MD -MP -MF .deps/ImageCache.Tpo -c ImageCache.c -o ImageCache.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT Label.lo -MD -MP -MF ".deps/Label.Tpo" -c -o Label.lo Label.c; \
	then mv -f ".deps/Label.Tpo" ".deps/Label.Plo"; else rm -f ".deps/Label.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Label.lo -MD -MP -MF .deps/Label.Tpo -c Label.c  -fPIC -DPIC -o .libs/Label.o
Label.c: In function 'LabelGetValue':
Label.c:2922: warning: missing sentinel in function call
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT Label.lo -MD -MP -MF .deps/Label.Tpo -c Label.c -o Label.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT LabelG.lo -MD -MP -MF ".deps/LabelG.Tpo" -c -o LabelG.lo LabelG.c; \
	then mv -f ".deps/LabelG.Tpo" ".deps/LabelG.Plo"; else rm -f ".deps/LabelG.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT LabelG.lo -MD -MP -MF .deps/LabelG.Tpo -c LabelG.c  -fPIC -DPIC -o .libs/LabelG.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT LabelG.lo -MD -MP -MF .deps/LabelG.Tpo -c LabelG.c -o LabelG.o >/dev/null 2>&1
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT List.lo -MD -MP -MF ".deps/List.Tpo" -c -o List.lo List.c; \
	then mv -f ".deps/List.Tpo" ".deps/List.Plo"; else rm -f ".deps/List.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT List.lo -MD -MP -MF .deps/List.Tpo -c List.c  -fPIC -DPIC -o .libs/List.o
In file included from /usr/include/X11/Xft/Xft.h:41,
                 from XmRenderTI.h:46,
                 from List.c:86:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from XmRenderTI.h:46,
                 from List.c:86:
/usr/include/X11/Xft/Xft.h:42:10: error: #include expects "FILENAME" or <FILENAME>
In file included from XmRenderTI.h:46,
                 from List.c:86:
/usr/include/X11/Xft/Xft.h:62: error: expected '=', ',', ';', 'asm' or '__attribute__' before '_XftFTlibrary'
/usr/include/X11/Xft/Xft.h:96: error: expected specifier-qualifier-list before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:103: error: expected specifier-qualifier-list before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:200: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:305: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:364: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'XftLockFace'
/usr/include/X11/Xft/Xft.h:403: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:409: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:418: error: expected declaration specifiers or '...' before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:419: error: expected declaration specifiers or '...' before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:428: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'XftCharIndex'
/usr/include/X11/Xft/Xft.h:461: error: expected ';', ',' or ')' before '*' token
List.c: In function 'ListQuickNavigate':
List.c:7432: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
List.c:7433: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
List.c: In function 'FirstChar':
List.c:7480: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
List.c:7491: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
make[3]: *** [List.lo] Error 1
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/lib/Xm'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/lib/Xm'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/lib'
make: *** [all-recursive] Error 1
sean@laptop:~/Desktop/openmotif-2.3.0$ 

```

---

### Post by snwagner on 2009-01-28
And here's my make install:
```
Making install in bindings
make[1]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/bindings'
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/bindings'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/X11/bindings" || mkdir -p -- "/usr/lib/X11/bindings"
 /usr/bin/install -c -m 644 'xmbind.alias' '/usr/lib/X11/bindings/xmbind.alias'
 /usr/bin/install -c -m 644 'acorn' '/usr/lib/X11/bindings/acorn'
 /usr/bin/install -c -m 644 'apollo' '/usr/lib/X11/bindings/apollo'
 /usr/bin/install -c -m 644 'dec' '/usr/lib/X11/bindings/dec'
 /usr/bin/install -c -m 644 'dg_AViiON' '/usr/lib/X11/bindings/dg_AViiON'
 /usr/bin/install -c -m 644 'doubleclick' '/usr/lib/X11/bindings/doubleclick'
 /usr/bin/install -c -m 644 'hal' '/usr/lib/X11/bindings/hal'
 /usr/bin/install -c -m 644 'hitachi' '/usr/lib/X11/bindings/hitachi'
 /usr/bin/install -c -m 644 'hp' '/usr/lib/X11/bindings/hp'
 /usr/bin/install -c -m 644 'ibm' '/usr/lib/X11/bindings/ibm'
 /usr/bin/install -c -m 644 'intergraph' '/usr/lib/X11/bindings/intergraph'
 /usr/bin/install -c -m 644 'intergraph17' '/usr/lib/X11/bindings/intergraph17'
 /usr/bin/install -c -m 644 'megatek' '/usr/lib/X11/bindings/megatek'
 /usr/bin/install -c -m 644 'motorola' '/usr/lib/X11/bindings/motorola'
 /usr/bin/install -c -m 644 'ncr_at' '/usr/lib/X11/bindings/ncr_at'
 /usr/bin/install -c -m 644 'ncr_vt' '/usr/lib/X11/bindings/ncr_vt'
 /usr/bin/install -c -m 644 'pc' '/usr/lib/X11/bindings/pc'
 /usr/bin/install -c -m 644 'sgi' '/usr/lib/X11/bindings/sgi'
 /usr/bin/install -c -m 644 'sni' '/usr/lib/X11/bindings/sni'
 /usr/bin/install -c -m 644 'sni_97801' '/usr/lib/X11/bindings/sni_97801'
 /usr/bin/install -c -m 644 'siemens_9733' '/usr/lib/X11/bindings/siemens_9733'
 /usr/bin/install -c -m 644 'siemens_wx200' '/usr/lib/X11/bindings/siemens_wx200'
 /usr/bin/install -c -m 644 'sony' '/usr/lib/X11/bindings/sony'
 /usr/bin/install -c -m 644 'sun' '/usr/lib/X11/bindings/sun'
 /usr/bin/install -c -m 644 'sun_at' '/usr/lib/X11/bindings/sun_at'
 /usr/bin/install -c -m 644 'tek' '/usr/lib/X11/bindings/tek'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/bindings'
make[1]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/bindings'
Making install in bitmaps
make[1]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/bitmaps'
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/bitmaps'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/X11/bitmaps" || mkdir -p -- "/usr/include/X11/bitmaps"
 /usr/bin/install -c -m 644 'xm_error' '/usr/include/X11/bitmaps/xm_error'
 /usr/bin/install -c -m 644 'xm_hour16' '/usr/include/X11/bitmaps/xm_hour16'
 /usr/bin/install -c -m 644 'xm_hour16m' '/usr/include/X11/bitmaps/xm_hour16m'
 /usr/bin/install -c -m 644 'xm_hour32' '/usr/include/X11/bitmaps/xm_hour32'
 /usr/bin/install -c -m 644 'xm_hour32m' '/usr/include/X11/bitmaps/xm_hour32m'
 /usr/bin/install -c -m 644 'xm_information' '/usr/include/X11/bitmaps/xm_information'
 /usr/bin/install -c -m 644 'xm_noenter16' '/usr/include/X11/bitmaps/xm_noenter16'
 /usr/bin/install -c -m 644 'xm_noenter16m' '/usr/include/X11/bitmaps/xm_noenter16m'
 /usr/bin/install -c -m 644 'xm_noenter32' '/usr/include/X11/bitmaps/xm_noenter32'
 /usr/bin/install -c -m 644 'xm_noenter32m' '/usr/include/X11/bitmaps/xm_noenter32m'
 /usr/bin/install -c -m 644 'xm_question' '/usr/include/X11/bitmaps/xm_question'
 /usr/bin/install -c -m 644 'xm_warning' '/usr/include/X11/bitmaps/xm_warning'
 /usr/bin/install -c -m 644 'xm_working' '/usr/include/X11/bitmaps/xm_working'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/bitmaps'
make[1]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/bitmaps'
Making install in config
make[1]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config'
Making install in cf
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/cf'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/cf'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/cf'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/cf'
Making install in imake
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/imake'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/imake'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/imake'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/imake'
Making install in makedepend
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/makedepend'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/makedepend'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/makedepend'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/makedepend'
Making install in util
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/util'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config/util'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/util'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config/util'
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/config'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config'
make[1]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/config'
Making install in localized
make[1]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/localized'
Making install in util
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/localized/util'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/localized/util'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/localized/util'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/localized/util'
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/localized'
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/localized'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/localized'
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/localized'
make[1]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/localized'
Making install in lib
make[1]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/lib'
Making install in Xm
make[2]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/lib/Xm'
make  install-am
make[3]: Entering directory `/home/sean/Desktop/openmotif-2.3.0/lib/Xm'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\"     -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2     -MT List.lo -MD -MP -MF ".deps/List.Tpo" -c -o List.lo List.c; \
	then mv -f ".deps/List.Tpo" ".deps/List.Plo"; else rm -f ".deps/List.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I. -I.. -I./.. -DXMBINDDIR_FALLBACK=\"/usr/lib/X11/bindings\" -DINCDIR=\"/usr/include/X11\" -DLIBDIR=\"/usr/lib/X11\" -g -O2 -Wall -g -fno-strict-aliasing -Wno-unused -Wno-comment -fno-tree-ter -I/usr/include/freetype2 -MT List.lo -MD -MP -MF .deps/List.Tpo -c List.c  -fPIC -DPIC -o .libs/List.o
In file included from /usr/include/X11/Xft/Xft.h:41,
                 from XmRenderTI.h:46,
                 from List.c:86:
/usr/include/ft2build.h:56:38: error: freetype/config/ftheader.h: No such file or directory
In file included from XmRenderTI.h:46,
                 from List.c:86:
/usr/include/X11/Xft/Xft.h:42:10: error: #include expects "FILENAME" or <FILENAME>
In file included from XmRenderTI.h:46,
                 from List.c:86:
/usr/include/X11/Xft/Xft.h:62: error: expected '=', ',', ';', 'asm' or '__attribute__' before '_XftFTlibrary'
/usr/include/X11/Xft/Xft.h:96: error: expected specifier-qualifier-list before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:103: error: expected specifier-qualifier-list before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:200: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:305: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:364: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'XftLockFace'
/usr/include/X11/Xft/Xft.h:403: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:409: error: expected ';', ',' or ')' before '*' token
/usr/include/X11/Xft/Xft.h:418: error: expected declaration specifiers or '...' before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:419: error: expected declaration specifiers or '...' before 'FT_UInt'
/usr/include/X11/Xft/Xft.h:428: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'XftCharIndex'
/usr/include/X11/Xft/Xft.h:461: error: expected ';', ',' or ')' before '*' token
List.c: In function 'ListQuickNavigate':
List.c:7432: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
List.c:7433: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
List.c: In function 'FirstChar':
List.c:7480: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
List.c:7491: warning: ignoring return value of 'mbtowc', declared with attribute warn_unused_result
make[3]: *** [List.lo] Error 1
make[3]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/lib/Xm'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/lib/Xm'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sean/Desktop/openmotif-2.3.0/lib'
make: *** [install-recursive] Error 1

```

---

### Post by kevdog on 2009-01-28
Im currently working towards a solution but still getting errors.  I was however able to download, configure, compile and install the openmotif cvs version (with no errors!!).  I'm still get Xlt make errors, however the make process is proceeding much farther along until I get the errors.  I'm probably missing some dependency library.  Currently at my real job, and will not have time to work on this until later tonight.  I think Im going to have to try to compile the cvs xlt sources.

---

### Post by snwagner on 2009-01-28
just seeing if you came up with anything.   Appreciate your help on this!

---

### Post by kevdog on 2009-01-29
Yes

I have successfully downloaded, compiled, and installed thus far openmotif and Xlt from cvs sources.  Ive currently downloaded XmBlackBerry from cvs and am in the process of compiling this as we speak.  So far so good I guess.

---

### Post by kevdog on 2009-01-29
Well got a little bit farther after a bit of frustration.

Problem: Couldn't compile libusb from cvs (major problem)

Workaround:

Had to do the following:
Downloaded CVS sources of XmBlackBerry
Downloaded latest release of XmBlackBerry.  Copied the the libusb directory from this release into the CVS directory

For example
cp -R ~/src/xmblackberry-0.3.0 ~/src/XmBlackBerry

Was then able to compile and install XmBlackBerry from CVS sources.

Last thing to do is to install the Barry library which I might try tomorrow.  This whole thing is a pain!

---

### Post by snwagner on 2009-01-29
Ok...  How do I do CVS?  Is there a tutorial on this?

---

### Post by snwagner on 2009-01-29
Ok... I managed to get openmotif 2.3 installed (I used alien to convert the .rpm to a .deb and it installed perfectly..)  Only problem is... when I run the ./configure for xmblackberry it doesn't recognize xlt as being installed, nor does it recognize openmotif as being correct version (at the very end of the ./configure it shows that I need to visit openmotif and I need to visit xlt)

---

### Post by snwagner on 2009-01-29
Please help!!!

---

### Post by snwagner on 2009-01-29
I got it: [http://ubuntuforums.org/showthread.php?t=1054698](http://ubuntuforums.org/showthread.php?t=1054698)

---

### Post by kevdog on 2009-01-30
Dont do the alien command -- Ive never found that very useful. Uninstall openmotif you installed this way, since its no good.  

Reference Webpages:
XmBlackBerry - [http://xmblackberry.sourceforge.net/](http://xmblackberry.sourceforge.net/)
Barry - [http://www.netdirect.ca/software/packages/barry/cvs.php](http://www.netdirect.ca/software/packages/barry/cvs.php)
Historical Installation Help (Much of these pages are outdated):
[INDENT][http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux](http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux)
[http://ubuntuforums.org/showthread.php?p=4550979](http://ubuntuforums.org/showthread.php?p=4550979)
[/INDENT]

Install dependencies (I've copied most of this list from other websites so I can not verify the accuracy of the entire list.  In the worst case it will install unnecessary libraries):

```

sudo aptitude install libc6-dev g++ gcc make build-essential
sudo aptitude install libtool autoconf automake cvs libglib2.0-dev libxml2-dev libssl-dev libopensync0-dev libxt-dev x11proto-print-dev libxmu-dev libxft-dev libfreetype6-dev libXp-dev flex byacc libgd2-xpm-dev libxaw-headers libxaw7-dev libreadline5 libreadline5-dev

```

Additional libraries I found needed to be installed

```
sudo aptitude install git libglademm-2.4-dev libgtkmm-2.4-dev libtar-dev doxygen
```


[SIZE="3"]
**OpenMotif**[/SIZE]

```

mkdir -p ~/src
cd ~/src
cvs -z3 d:pserver:anonymous@openmotif.cvs.sourceforge.net:/cvsroot/openmotif co openmotif
cd openmotif
./autogen.sh
./configure
make
sudo make install

```


**[SIZE="3"]libXLT[/SIZE]**

```

cd ~/src
cvs -d :pserver:anonymous@xlt.cvs.sourceforge.net:/cvsroot/xlt co Xlt
cd Xlt
./CVSMake
./configure
make
sudo make install

```

Additional command needed to make libXlt accessible by the XmBlackBerry package (64 bit only):
```

sudo ln -s /usr/local/lib/libXlt.so.21 /usr/lib/x86_64-linux-gnu/libXlt.so.21

```

**[SIZE="3"]XmBlackberry[/SIZE]**

(Installation of XmBlackberry depends of libusb.  Unfortunately the compilation of libusb from cvs sources is broken for me.  So hence a bit of trickery is needed to get a working copy of libusb.  For me this required downloading the cvs sources of XmBlackBerry along with the last release candidate of XmBlackBerry which contained libusb in the release.  I then simply copied the libusb folder from the release version to the cvs version to make this work)

**[SIZE="2"]Download XmBlackBerry from CVS[/SIZE]**

```

cd ~/src
cvs -d:pserver:anonymous@xmblackberry.cvs.sourceforge.net:/cvsroot/xmblackberry co XmBlackBerry

```

**[SIZE="2"]Download XmBlackBerry release version[/SIZE]**
Alternative Link Site: [http://sourceforge.net/project/showfiles.php?group_id=165059&package_id=187091&release_id=539674](http://sourceforge.net/project/showfiles.php?group_id=165059&package_id=187091&release_id=539674)

```

cd ~/src
wget 'http://downloads.sourceforge.net/xmblackbery/xmblackberry-0.3.0.tar.gz?modtime=1189847430&big_mirror=0'
tar zxvf xmblackberry-0.3.0.tar.gz

```

**[SIZE="2"]Copy the libusb directory from the xmblackberry release package to the cvs XmBlackBerry tree[/SIZE]**

```
cp -R ~/src/xmblackberry-0.3.0/libusb ~/src/XmBlackBerry
```

**[SIZE="2"]Compile and Install XmBlackberry from CVS[/SIZE]**

```

cd ~/src/XmBlackBerry
./CVSMake
./configure
make
sudo make install

```

**[SIZE="2"]Install libusb explicitly[/SIZE]**

```

cd libusb
sudo make install

```


**[SIZE="3"]Barry[/SIZE]**

```

cd ~/src
git clone git://repo.or.cz/barry.git barry
cd barry
./buildgen.sh cleanall
./buildgen.sh
./configure
make
sudo make install
doxygen

**Optional for gui plugin:**
[INDENT]cd gui
./configure
make
sudo make install
[/INDENT]

```

---

### Post by radostyle on 2009-01-30
Thanks Kevdog.  I have been trying for a while to compile this from the old documentation and was stuck, your instructions worked great.  

Slight errors were (in the openmotif install)
```

cvs -z3 d:pserver:anonymous@openmotif.cvs.sourceforge.net:/cvsroot/openmotif co openmotif
```

is missing the dash in front of the d and should be
```

cvs -z3 -d:pserver:anonymous@openmotif.cvs.sourceforge.net:/cvsroot/openmotif co openmotif

```
also in the xmblackberry release download
```

wget http://downloads.sourceforge.net/xmblackbery/xmblackberry-0.3.0.tar.gz?modtime=1189847430&big_mirror=0
```

the ampersand causes the command to go into the background and doesn't actually download file, so I had to go to sourceforge and download the file.
[http://sourceforge.net/project/showfiles.php?group_id=165059&package_id=187091&release_id=539674](http://sourceforge.net/project/showfiles.php?group_id=165059&package_id=187091&release_id=539674)
  I haven't yet tested the actual tethering, but everything is compiled now.  I am on an Ibex 64-bit install.

---

### Post by kevdog on 2009-01-30
Thanks for clarifications -- lets see if I can get that wget statement to work correctly ;)

---

### Post by radostyle on 2009-01-30
I ran
```
/usr/local/bin/XmBlackBerry 

```

and got this error

```
/usr/local/bin/XmBlackBerry: error while loading shared libraries: libXlt.so.21: cannot open shared object file: No such file or directory

```

so I ran

```
 strace /usr/local/bin/XmBlackBerry
```

to see where it was looking for the file and I had to create a symlink

```
sudo ln -s /usr/local/lib/libXlt.so.21 /usr/lib/x86_64-linux-gnu/libXlt.so.21
```

after that my XmBlackBerry came up.  Not sure why I was missing that.

---

### Post by radostyle on 2009-01-30
Success...

Woohoo.  This is sent from my tethered blackberry.  Thanks again Kevdog!

---

### Post by kevdog on 2009-01-30
I wonder if the symbolic link you needed to create was because you are on a 64 bit install?  Strange.  I wish there were more people to test the code.

---

### Post by tcolar on 2009-03-12
I'm the author of the original Howto you used, which was based on my work here:
[http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux](http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux)

Just wanted to mention that I made a new (way simpler to use - no compilation) program called bbtether, dedicated to tethering a BB.

[http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)

---

