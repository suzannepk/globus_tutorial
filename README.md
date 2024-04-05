# Globus Tutorial
Below are notes to build the tutorial. This is a work in progress. 

This shows how to use and script globus with OLCF collections (endpoints).
Collections are portals in to the OLCF filesystems that allow you to transfer data useing  a single sign on with your OLCF user ID and Passcode, 
That will allow the collection to remain active for trasfers without reauthentication for seveal days. 
If you familuare with using globus verion 4, collection give you the same functionallity as "endpoints". 

For this tutorial we will use Globus_Cli to move a file from one on Globus's test collection to OLCF. 

Login to globus via the webinterface globus.org. 

If you do not have a globis ID you can follow the links to set one up. 

Once you are logged into globus.org. You will see a collections search bar. 

To find the OLCF DTN (Globus5), type OLCF DTN and a list of OLCF endpoints will appear. 
Select the the OLCF DTN (Globus5) from the list. 

Globus will take you back to the file manager and tell you that you need to login to autheticate to that endpoint. 
Click continue. 
If this is the first time you have ever done this for any given endpoint, globus will ask you to link your globus ID to the 
host organization's SSO. Follow the prompts to do so. The Globus will take you to the sgin in page for the SSO. 

Sign in to the OLCF SSO with your OLCF username and password. 

The collection 

. . . 

You must first install globus_ on the systems that you want to use it. 

You can put it in your home or project directory 

$ module load cray-python 
$ python3 -m venv /ccs/proj/stf007/globus_cli
$ source /ccs/proj/stf007/globus_cli/bin/activate
$ pip install globus-cli

Note you need to see if there is a more vanilla python that will allow you to use it on DTNS and Andes. 
There is not- you need a venv for each machine 



-----
```
$ globus login 
```
Globus will give you url that you must paste into your browser and use to authenticate. 
The authentication will give you a code that you eneter on the commandline. 

```
globus endpoint search 'OLCF'
export olcfdtn=36d521b3-c182-4071-b7d5-91db5d380d42
```
globus ls "$olcfdtn:/ccs/home/suzanne"
 1009  globus session update sso.ccs.ornl.gov clients.auth.globus.org
 1010  globus session show 
 1011  globus ls "$olcfdtn:/ccs/home/suzanne"
 1012  history 
 1013  globus mkdir "$olcfdtn:/ccs/home/suzanne/liea"
 1014  globus transfer "$olcfdtnt:/ccs/home/suzanne/vec*" "$olcfdtn:/ccs/home/suzanne/liea/"
 1015  globus transfer "$olcfdtnt:/ccs/home/suzanne/vec_add.f90" "$olcfdtn:/ccs/home/suzanne/liea/"
 1016  globus transfer "$olcfdtn:/ccs/home/suzanne/vec_add.f90" "$olcfdtn:/ccs/home/suzanne/liea/"

 Moves direcory every min for eterntiy 
globus timer create transfer --interval 1m --recursive $olcf:/ccs/home/suzanne/start/ $olcf:/ccs/home/suzanne/transferred/

had to use the web interface to turn it off. 







