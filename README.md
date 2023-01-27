# MAP3270-V3.0.0 Full install (including source code) for MVS 38j systems running Hercules 
TK3 or TK4- systems.

All the executable code is provided so the install just involves submitting some JCL and
a couple of edits.
This project contains the complete source code for generating the MAP3270 project from source code
at your option.

MAP3270 V2.x.x is pre-installed on distributions of TK4- V8.  Some of the executables are in ‘SYS2.LINKLIB’.
Others are in MAP3270.LOADLIB on volume PUB000.
All the other datasets have the high level qualifier ‘MAP3270.’
No version of MAP3270 is pre-installed on distributions of TK3.

These instruction will create what I call a “test version”.  All the dataset are created with the 
high level qualifier ‘userid.MAP3270’.  If you desire, the JCL can be modified to directly update 
the TK4- pre-installation.  I recommend creating the “test” version and then copy the all the 
members to update the TK4- pre-installation.

All of the .txt files are compile listings and/or installation listings.  The .pdf files 
are documentation.

All steps in each job must complete with RC= 0000 except for COBOL and PL/I compiles, which can 
complete with RC= 0004.

STEP 1
======
Download the MAP3270-V2.2.0.aws file.  This is a hercules tape with a vol ser of MP3270.

STEP 2
======
Using HERCULES, assign MAP3270-V2-2-0.aws to unit 0480.  This can be done via 
the .cnf file or devinit console command.

STEP 3
======
Edit RESTORE.JCL if you may want to change the default userid HERC01, volume PUB002  
and the tape drive for the tape (assumed to be 480).  All steps should end with RC = 0000.  
This job will create backup copies of the datasets that will be created.  The backup copies
will have a .OLD. inserted into the DSN.

The following data sets will be created:
userid.MAP3270.ASM  
userid.MAP3270.CNTL
userid.MAP3270.COB
userid.MAP3270.MACLIB
userid.MAP3270.MAP
userid.MAP3270.PANEL
userid.MAP3270.PANEL5
userid.MAP3270.PLI
userid.MAP3270.SOURCE
userid.MAP3270.SOURCE5
userid.MAP3270.LOADLIB

STEP 4
======
When restore is successfully completed, the "test" install is completed.  Option: you could
submit userid.MAP3270.CNTL(COMPILE_) where _ is 1,2 or 3 to recompile the entire package less 
the demo programs.
Submit userid.MAP3270.CNTL(COMPILE4) to recompile the demo programs.

STEP 5
======
Refer to the MAP3270 Tutorial.pdf for additional installation steps that must be completed
manually.  For an initial install, these manual steps must be completed.  
For an update install, verify that the changes were made.


=======================================================================
=======================================================================
