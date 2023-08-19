# notes
---------------------under AppServer/bin/ ------------------------------------

./manageprofiles.sh -create -profileName Dmgr01 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/dmgr -serverType DEPLOYMENT_MANAGER -hostName host01 -enableAdminSecurity true -adminUserName wasadmin -adminPassword wasadmin

---------[ start Dmgr01 ] ----------------------------------------------------------------

./manageprofiles.sh -create -profileName sp1 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/default -enableAdminSecurity true -adminUserName wasadmin -adminPassword wasadmin -serverName s1 -nodeName Node01

./manageprofiles.sh -create -profileName sp2 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/default -enableAdminSecurity true -adminUserName wasadmin -adminPassword wasadmin -serverName s2     -nodeName Node02

------------------under bin dir of app_server_id ----------------------------------------

./addNode.sh  host01 8879 -conntype SOAP -includeapps -username wasadmin -password wasadmin

------------------------------------ stand alone profile----------------------------
./manageprofiles.sh -create -profileName sp3 -templatePath /opt/WAS/profileTemplates/default -enableAdminSecurity true -adminUserName wasadmin -adminPassword wasadmin -serverName s3     -nodeName Node03  -hostName host01 -cellName Cell03
------------------------------------------------------------------------------------
nodejs
-------------------------------------------------------------------------------------
npm update --save/--save-dev
npm start

---------------------------------------------
ibm http server ssl & rewrite
---------------------------------------------
LoadModule ibm_ssl_module modules/mod_ibm_ssl.so
Listen 443
SSLCheckCertificateExpiration 30
<VirtualHost *:443>
 SSLEnable
</VirtualHost>
KeyFile /opt/IHS/ssl/ihskey.kdb
LoadModule rewrite_module modules/mod_rewrite.so
<VirtualHost *:80>
RewriteEngine on
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{SERVER_NAME}/
</VirtualHost>

----------------------------------------------------------------------------------------
