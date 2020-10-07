---
title: SMS Api horisen sit
url: /sms-api-horisen-sit
---
# HORISEN SIT API

## Introduction 

#### What specifically does this API endpoint do?

In order to create variety of different documents, you should consider going through this API documentation.  

Horisen SIT API is used by HORISEN applications for Finance Documents.
This API returns a list of documents for given parameters with all their items. 

## Authentication 

#### Oauth2 Authentication

HORISEN.pro APIs use the OAuth 2.0 protocol for authentication. HORISEN.pro supports common OAuth 2.0 scenarios such as those for machine2api or user2api access.

These are main steps to have your application up and running: 

1. **Register application and obtain credentials** 

    You need to provide you app information for our support team: name, redirect url (only for client-side applications), ip address(es) from which your app accesses our APIs (only for server-side applications)  
    
    In return you will be given client_id, client_secret which must be stored securely on your server.

2. **Implement authentication to obtain access token**

    There are two diferrent flows and the one to be used depends on the nature of you app. **Authorization code grant** - should be used when an user is present to interact (login and approve) app access. This is similar how Google, Facebook social login and api access work.  
    **Client credentials grant** - suitable for machine-to-machine authentication, for example for use in a cron job which is performing maintenance tasks over an API. Another example would be a client making requests to an API that don't require user's interaction.

3. **Call HORISEN.pro API endpoints** 
 
Having valid access token you are ready to access API endpoints of your choice. Here's example curl call which adds new contact in your nGage Customer Data Store. 


## Domain 

This API belongs to the Finance domain. Subject 
Domain in the endpoint url is: 

/finance/sit/v1

## HTTP Call Type Definitions

Our SIT API for the finance documents is based on the GET method - Used to retrieve a representation of a resource.  
In the following lines, we will describe its functionalities and resources. 


## Get method  

Returns list of documents for export. This endpoint accepts query parameters for filtering documents described in separate document. 

### Parameters



| Name | Type | Description | 
|--------|-----|---------- |
|   page_number | integer  | Page number - Default value = 1 |
|   page_size | integer  | Page number - Default value = 10 |
|   paging | string  | paging options in form of &paging=page_num,page_size. <p> **Example**: If we put “paging=1,10” as query parameter API will return first ten items. |
|   operator(fieldName) | string  | <p> Search criteria using following operators : <ul><li>isnull</li><li>isnotnull</li><li>isempty</li><li>isnotempty</li><li>eq</li><li>neq</li><li>startswith</li><li>contains</li><li>endswith</li><li>doesnotcontain</li><li>lt</li><li>lte</li><li>gt</li><li>gte</li><li>in</li><li>notin</li><li>between</li><li>notbetween</li></ul>  <p> **And by following attributes**: <ul><li>documentUuid</li><li>id</li><li>instanceId</li><p> <p><li>bizPartnerId</li><li>bizPartnerCountry</li><li>bizPartnerExternalRefId</li> <p> <li>documentDate</li><li>deliveryDate</li><li>documentNumber</li><li>documentNumberNum</li><li>dueDate</li><li>periodStart</li><li>periodEnd</li><li>currency</li><li>currencyCode</li> <p></p> <li>amountNoVat</li><li>amountVat</li><li>vatPercent</li><li>vat</li><li>rounding</li><li>total</li><li>totalUnpaid</li><li>totalPaid</li> <p> <li>domesticCurrency</li><li>domesticCurrencyCode</li><li>domesticCurrencyRate</li><li>domesticAmountNoVat</li><li>domesticAmountVat</li><li>domesticRounding</li><li>domesticTotal</li> <p> <li>status</li><li>insertDt</li><li>statusDt</li><li>paymentStatus</li><li>paymentStatusDate</li> <p> <li>lang</li><li>documentType</li><li>documentTypeName</li><li>selfBilling</li><li>domainId</li> <p> <li>domainCodeName</li><li>dataSourceId</li><li>dataSourceCodeName</li><li>documentClassCodeName</li><li>documentClassDomain</li><li>documentClassArea</li><li>dataSourceSelector</li> <p> <li>syncStatus</li><li>syncStatusDt</li><li>disputeStatus</li><li>docsDeliveryStatus</li> <p> **If operator is one of**: isnull , isnotnull, isempty, isnotempty - field value can be ommited. <p> If operator is **in** or **notin** field value must be coma separated list of values. <p> If operator is **between** or **notbetween** field value must be coma separated list of two values representing beginng and the end of range. <p> Operator can be ommited and in that case it will be treated as operator is eq (Eg: fieldName=fieldValue) <p> **Example**: startswith(clientName)=hor, starts with hor in field clientName if fieldName is q and operator is eq or ommited, field value will be used in general search across multiple attributes.|
|   sort | string  | sort options in form of sort=-attribute1,attribute2,-attribute3 <p> **Sort available fields**:<ul><li>documentUuid</li><li>id</li><li>instanceId</li> <p> <li>bizPartnerId</li><li>bizPartnerCountry</li><li>bizPartnerExternalRefId</li><li>bizPartnerName</li><li>bizPartnerBriefName</li><li>bizPartnerType</li><li>bizPartnerAttn</li><li>bizPartnerAddress</li><li>bizPartnerPost</li><li>bizPartnerCity</li><li>bizPartnerVatNumber</li> <p> <li>documentDate</li><li>deliveryDate</li><li>documentNumber</li><li>documentNumberMask</li><li>documentNumberNum</li><li>dueDate</li><li>periodStart</li><li>periodEnd</li> <p> <li>currency</li><li>currencyCode</li><li>amountNoVat</li><li>amountVat</li><li>vatPercent</li><li>vat</li><li>rounding</li><li>total</li><li>totalUnpaid</li><li>totalPaid</li> <p> <li>domesticCurrency</li><li>domesticCurrencyCode</li><li>domesticCurrencyCode</li><li>domesticCurrencyRate</li><li>domesticAmountNoVat</li><li>domesticAmountVat</li><li>domesticRounding</li><li>domesticTotal</li> <p> <li>status</li><li>insertDt</li><li>statusDt</li><li>paymentStatus</li><li>paymentStatusDate</li><li>lang</li><li>documentType</li><li>documentTypeName</li><li>domainId</li><li>domainCodeName</li> <p> <li>dataSourceId</li><li>dataSourceCodeName</li><li>documentClassCodeName</li><li>documentClassDomain</li><li>documentClassArea</li><li>dataSourceSelector</li> <p> <li>syncStatus</li><li>syncStatusDt</li><li>disputeStatus</li><li>docsDeliveryStatus</li></ul> | 



### Responses 


| Code | Description  | Links |
|--------|-----|
|   200 | 	[Horisen SIT Api](#sit-api)  | No links |
| default |  [List of errors](#error-list) | No links |

#### Sit api



| Name | Type | Description | 
|--------|-----|
|   documentUuid | string | DocumentUuid is the unique uuid per document that each document will have. |
|   id | integer | The id is the unique key for the document in the table in which that document type is stored |
|   instanceId | integer | The application instance represents the "logical installation" of particular application. <p> The instance has an owner and belongs to one and only one context of the same owner. <p> The context defines a "group" of application instances of the same owner which represent an application platform. <p> InstanceId determines which platform and application the document belongs to. |
|   bizPartnerId | integer | Business Partner Id |
|   bizPartnerCountry | integer | Business Partner Country |
|   bizPartnerExternalRefId | string | BizPartnerExternalRefId is an optional foreign key to external db (independent resellers system). |
|   bizPartner | Object | [Business Partner Object(Click on this link for the further info)](#business-partner-object) |
|   documentDate | 	string($date) | Document date |
|   deliveryDate | 	string($date) | Delivery date |
|   documentNumber | 	string | Invoice number in the invoice |
|   documentNumberMask | 	string | Invoice number fix - from what number numeration will start |
|   documentNumberNum | 	integer| Ordinal number of the invoice |
|   dueDate | 	string($date) | Document date |
|   periodStart | 		string($date) | Start period date |
|   periodEnd | 	string($date) | End period date |
|   currency | 	integer | Currency number |
|   currencyCode | 	string| Name of the currency. eg. "EUR" |
|   amountNoVat |	number($float) | Document amount including VAT. Can be negative when selfBilling is 'yes'. |
|   vatPercent |	number($float) | Percentage of the value added tax |
|   vat |	number($float) | Value of the value added tax |
|   rounding |	number($float) | Difference between document total and amount including VAT value |
|   total |	number($float) | Document gross amount. Can be negative when selfBilling is 'yes' |
|   totalUnpaid |	number($float) | 
Document unpaid amount. |
|   totalPaid |	number($float) | Document paid amount. |
|   domesticCurrency |	integer | Domestic currency |
|   domesticCurrencyCode |	string | Domestic currency code. eg. "CHD" |
|   domesticCurrencyRate |	number($float) | Domestic currency rate used to calculate domestic currency amounts |
|   domesticAmountNoVat |	number($float)| Document amount in domestic currency without VAT|
|  domesticAmountVat	 |	number($float)| Document amount in domestic currency with VAT|
|  domesticRounding	 |	number($float)| Document rounding, difference between domestic currency total and domestic currency amount with VAT|
|  domesticTotal	 |	number($float)| Document total amount in domestic currency|
|  status	 |	string | Enum: draft, approved, rejected, canceled, archived, imported |
|  insertDt		 |	string($date-time)| Date-time of the insert|
|  statusDt	 |	string($date-time)| Status date-time |
|  paymentStatus	 |	string| enum: Array[4] |
|paymentStatusDate | string($date-time) | payment status date |
|domainId | integer  | Id of domain which represents business area, which further contains business processes that are related with data-sources. <p> The "business area" is very wide definition, here in our case we can map it to product or product_type (SMS and MNP).<p> |
|domainCodeName| string | DomainCodeName is code name of domain with given domainId. It can be BULK (for bulk sms) and BULK-MNP (for bulk mnp). |
|documentClassCodeName| string | Unique code name for easier recognition |
|documentClassDomain | string |  The group/section of documents (for now we only know for "invoice" domain) |
|documentClassArea| string | The business area/section, i.e. sales or purchase |
|selfBilling| string | Enum: Array [ 2 ]. SelfBilling indicates does certain document type represents self billing invoice.<p> In case of customer invoice, self billing means that invoice owner has to pay to customer, not vice versa (this is so called credit note).<p> Self billing document is paired with exactly one document type for "regular" document, on that way system exactly knows when during creating invoice gets negative total how to switch document type |
|dataSourceId| integer | Datasource id |
|datasourceCodeName| string | Code name from which this document originates |
|dataSourceSelector | string | Data source selector |
|dataSource| object | [Data Source Document Object(Click on this link for the further info)](#datasource-object).  |
|lang| string | lang |
|documentType| string | Every document has to have document type. Document types are defined on instance level because they hold settings on platform level. <p> One documentType has only one documentTypeName. Examples for documentTypeNames: <ul><li>'Bulk Invoices'</li><li>'Bulk Invoice - Prepaid Topup'</li><li>'Bulk Invoice - Postpaid'</li><li>'Prepaid Supplier Invoice'</li><li>'Netting Invoice'</li><li>'Self Billing of Netting Invoice'</li><li>'Bulk Postpaid Control Invoice'</li><li>'Invoice Debit Note'</li><li>...</li></ul> <p> |
|syncStatus|string |SyncStatus is document synchronization status. The synchronization is done between our system and some independent financial software. <p> Possible values are: **None** - syncing is never done nor in schedule <p> **Waiting** - waiting to start syncing <p> **Syncing** - syncing in progress, <p> **Done** - sucessfully done <p> **Exported** - document is exported, file to be imported into the external  system is sucessfully created <p> **Error** - some error happened during syncing <p> **Invalid** - syncing was "done" but after that source document is changes, so target document is out of sync (example: source document is canceled) <p> **Misc** - temporary status for internal use |
|syncStatusDt|string($date-time)|sync status date|
|disputeStatus|string|DisputeStatus indicates whether the invoice is in dispute process or not. <p> Possible values are: <p> **None** - the invoice is not in dispute process, <p> **Open** - the invoice is in dispute process and it is still not resolved <p> **Closed** - the invoice was in dispute process but it is resolved so invoice is again valid <p>|
|docsDeliveryStatus|string|Possible statuses are:  **none, waiting, sending, sent, error, misc** |
|docsDeliveryStatusDate|string($date-time)| Document delivery status date|
|Items|list of items|[List of Items(Click on this link for the further info)](#items-list)|

##### Business partner object
 

**Object description:
Business Partner object contains all the data related to the Business Partner** 

| Name | Type | Descrdaiption | 
|--------|-----|
|   name | string | Business Partner name |
|   briefName | string | Business Partner short name |
|   partnerType | string | Business Partner type |
|   attn | string | attn is property “Attention to Person” from biz partner address. |
|   post | string | Postal Code |
|   city | string | Name of the city |
|   vatNumber | string | Value added tax |
|   customAttributes | list |[List of custom attributes in the Business Partner Object(Click on this link for the further info)](#custom-attributes-for-business-partner) |

 
 
 

#### Custom attributes for business partner 

 **<p>Description:
Custom attributes are attributes that the user defines at the business partner level. They are used to enrich basic data in many sections (areas) of the business partners model.**

**Example: We can define a custom attribute Contract No. and then save some values for that field for some of the biz partners. For the partner that has value for this field, we will get in the CustomAttributes list object as follows: <p>**

{
	“codeName”: “CONTRACT_NO”,
	“value”: “123456”
}


| Name | Type | Description | 
|--------|-----|
|   codeName | STRING_EXAMPLE | Business Partner name |
|   value | value "" | Value |
|   codeName | OBJECT_EXAMPLE | Business Partner Code Name as a object |
|   value | string | Value |
|   propertyA | value "" | Value of property "" |
|   propertyB | value "" | Value of property "" |
 

#### Datasource object

**Object description:** <P> 	
If document dataSourceCodeName is POSTPAID and dataSourceSelector is empty
DataSourceDocument will contain id which is id of related billing record and object billingTotalBalance
If document dataSourceCodeName is POSTPAID and dataSourceSelector is PART-PAYMENT or dataSourceCodeName is PREPAID
DataSourceDocument will contain id which is id of related credit record and object billingTotalBalance
In all other cases DataSourceDocument will be null <p> <br> 

| Name | Type | Description | 
|--------|-----|
|   id | integer | id is the billing record Id associated with the document. Currently only available for postpaid invoices |
|   billingTotalBalance | object | [billing total balance Object(Click on this link for the further info)](#billing-total-balance-object) |



#### Billing total balance object

**Object description: BillingTotalBalance is Invoice Condition to which document is associated to.**

| Name | Type | Description | 
|--------|-----|
|   id | integer | Id is the billing record Id associated with the document |
| instanceId | integer | The application instance represents the "logical installation" of particular application. |
| bizPartnerId |integer | Business partner Id|
| currency | integer | Currency number|
| currencyCode |string | Currency code. eg. "EUR"|
| billingTypeCodeName |string | Billing type code name |
| name |string | Name |
| customAttributes | list |example: List [ OrderedMap { "codeName": "STRING_EXAMPLE", "value": "value C" }, OrderedMap { "codeName": "OBJECT_EXAMPLE", "value": OrderedMap { "propertyA": "value A", "propertyB": "value B" } }  ] |
 

#### Items list

**Description: List of Items contains fields related to the invoice.**

| Name | Type | Description | 
|--------|-----|
|   id | integer | id of the item |
|   documentId | integer | DocumentID is id of the document to which the item belongs, the id property of the Document object. This property is the same for all items belonging to the same document. |
|   ordNum | integer | Ordinary number |
|   name | integer | Nname of the item |
|   quantity | number($float) | Quantity |
|   measureUnit | string | Measure unit |
|   price | number($float) | Price |
|   totalNoVat | 	number($float) | Total value without VAT |
|   totalVat | 	number($float) | Total value with VAT |
|   dataSourceId | integer | DataSourceID is the id of data source from which this item comes from. The most probably this will match with document dataSourceId, but we have it on item level to store explicitly pointer to data source which is originator of the item (on that way we can support in future (if needed) items for different data sources). |
|   dataSourceCodeName | string | Code name from which this document originates |
|   dataSourceForeignKey | integer | Foreign key|
|   dataSourceSelector | string | Data source selector |
|   dataSource | object | DataSource is the source from which this document item originates. It contains billing account object (billing account is pricing condition) related to that document item. [Data source doc item(Click on this link for the further info)](#datasource-document-item) |



#### Datasource document item

****Object descrition:** <p>  If item or document dataSourceCodeName is POSTPAID and dataSourceSelector is empty</br>
        DataSourceDocumentItem will contain id which is id of related charge record and object billingAccount</br>
        If item or document dataSourceCodeName is POSTPAID and dataSourceSelector is PART-PAYMENT</br>
        DataSourceDocumentItem will contain id which is id of related credit record and documentId which is id of related invoice</br> <p>**

| Name | Type | Description | 
|--------|-----|
|   id | integer | id of the datasource |
|   documentId | integer | id of the document |
|   billingAccount | object | id of the datasource. [billing account object(Click on this link for the further info)](#billing-account-object) |



#### Billing account object

**Description: Billing Account is Pricing Condition and it contains all the fields related to the specified pricing condition**

| Name | Type | Description | 
|--------|-----|
|   id | integer | id of the billingAccount |
|   instanceId | integer | The application instance represents the "logical installation" of particular application. The instance has an owner and belongs to one and only one context of the same owner. The context defines a "group" of application instances of the same owner which represent an application platform. InstanceId determines which platform and application the document belongs to. |
|   bizPartnerId | integer | businessPartner id |
|   currency | integer | currency number |
|   currencyCode | string | currency code. eg. "EUR" |
|   billingTypeCodeName | string | billing type code name  |
|   name | string | name |
|   customAttributes | object | <p> example: List [ OrderedMap { "codeName": "STRING_EXAMPLE", "value": "value C" }, OrderedMap { "codeName": "OBJECT_EXAMPLE", "value": OrderedMap { "propertyA": "value A", "propertyB": "value B" } } ] [billing account custom attributes fields(Click on this link for the further info)](#billing-account-custom-attributes) <p> |
|   smsConnection | object | sms connection object related to the specific billing account. [smsConnection object fields(Click on this link for the further info)](#sms-connection-object) |
|   mnpConnection | object | mnp connection object related to the specific billing account. [smsConnection object fields(Click on this link for the further info)](#mnp-connection-object) |


##### Billing account custom attributes

 

**Description:  Custom attributes are attributes that the user defines at the Billing Account level. They are used to enrich basic data in many sections (areas) of the billing account model.**

 **Example: We can define a custom attribute codeName and then save some values for that field for some of the Billing Accounts.** 
 

| Name | Type | Description | 
|--------|-----|
|   codeName | string | code name |
|   value | string | <p> Property value can be a string or a json object <p>|
|   oneOf | string | additional explanation |


##### Sms connection object

**Object description** **:SMS Connection object has fields related to the specefied smsConnection in the Billing Account**

| Name | Type | Description | 
|--------|-----|
|   id | integer | sms connection id |
|   instanceId | integer | billing account id |
|   name | string | sms connection name |
|   authName | string | authentication name |
|   protocol | string | name of the protocol |

##### Mnp connection object

**Object description: MNP Connection object has fields related to the specefied MNP Connection in the Billing Account**

| Name | Type | Description | 
|--------|-----|
|   id | integer | sms connection id |
|   instanceId | integer | billing account id |
|   name | string | sms connection name |
|   authName | string | authentication name |
|   protocol | string | name of the protocol |

#### Error list


| Response code | Response body | Message | 
|--------|-----|
|    401 | NOT_AUTHENTICATED |  Not authenticated |
|    401 | NOT_AUTHORIZED |  Not authorized |
|    404 | BAD_PARAM |  Bad parameter |
|    400 | BAD_PARAM_PAGE_NUMBER |  Bad parameter 'page_number': value must be greather than 0 |
|    400 | BAD_PARAM_PAGE_SIZE |  Bad parameter 'page_size': value : must be greather than 0 |
|    500 | INT_APP_ERROR | FINANCE instance not found |
|    500 | INT_APP_ERROR |  BUSINESS_PARTNERS instance not found |
|    500 | INT_APP_ERROR |  Internal server error |
|    404 |INVOICE_NOTFOUND | Invoice not found |


### JSON Response Example 

1. **Part-payment Example**

``` 
{
	"data": [
		{
			"documentUuid": "f44d0a30-b28f-4641-854c-4bc50c7d7e56",
            "id": 22960,
            "instanceId": 41,
            "bizPartnerId": 87612478,
            "bizPartnerCountry": 384,
            "bizPartnerExternalRefId": "XZ876765-S33",
			"bizPartner": {
				"name": "Business Partner Example 1",
                "briefName": "BP 1",
                "partnerType": "wholesale",
                "attn": "",
                "address": "",
                "post": "",
                "city": "",
                "vatNumber": "",
                "customAttributes": [
                    {
                        "codeName": "OBJECT_EXAMPLE",
                        "value": {
                            "propertyA": "value A",
                            "propertyB": "value B"
                        }
                    }
                ]
			},
			"documentDate": "2019-09-30",
            "deliveryDate": "2019-09-30",
            "documentNumber": "300919-1",
            "documentNumberMask": "300919-%d",
            "documentNumberNum": 1,
            "dueDate": "2019-10-30",
            "periodStart": "2019-09-01",
            "periodEnd": "2019-09-30",
            "currency": 978,
            "currencyCode": "EUR",
            "amountNoVat": 0.55,
            "amountVat": 0.55,
            "vatPercent": 0,
            "vat": 0,
            "rounding": 0,
            "total": 0.55,
            "totalUnpaid": 0.55,
            "totalPaid": 0,
            "domesticCurrency": 752,
            "domesticCurrencyCode": "SEK",
            "domesticCurrencyRate": 10.7287,
            "domesticAmountNoVat": 5.9,
            "domesticAmountVat": 5.9,
            "domesticRounding": 0,
            "domesticTotal": 5.9,
            "status": "approved",
            "insertDt": "2019-10-01T11:08:59Z",
            "statusDt": "2019-10-01T16:33:05Z",
            "paymentStatus": "open",
            "paymentStatusDate": "2019-10-01T16:33:05Z",
            "domainId": 1,
            "domainCodeName": "BULK",
            "documentClassCodeName": "CUSTOMER_INVOICE",
            "documentClassDomain": "invoice",
            "documentClassArea": "sales",
            "selfBilling": "no",
            "dataSourceId": 2,
            "dataSourceCodeName": "POSTPAID",
			"dataSourceSelector": "PART-PAYMENT",
			"dataSource": {
				"id": 214,
				"billingTotalBalance": {
					"id": 1994,
					"instanceId": 12,
					"bizPartnerId": 87612478,
					"currency": 978,
					"currencyCode": "EUR",
					"billingTypeCodeName": "POSTPAID",
					"name": "BP1 postpaid CHF",
					"customAttributes": [
                        {
                            "codeName": "CONTRACT_NAME",
                            "value": "DD2000018"
                        }
                    ]
				}
			},
			"lang": "en",
			"documentType": 26,
			"documentTypeName": "Bulk Invoice - Postpaid Part Payment",
			"syncStatus": "none",
			"syncStatusDt": null,
			"disputeStatus": "none",
			"docsDeliveryStatus": "none",
			"docsDeliveryStatusDate": null,
			"items": [
				{
					"id": 99091,
					"documentId": 22960,
					"ordNum": 1,
					"name": "Postpaid Bulk SMS Part Payment\nPostpaid EUR",
					"quantity": 0,
					"measureUnit": "PIECE",
					"price": 0,
					"totalNoVat": 0.552,
                    "totalVat": 0.552,
					"dataSourceId": 2,
					"dataSourceCodeName": "POSTPAID",
					"dataSourceForeignKey": 214,
					"dataSourceSelector": "PART-PAYMENT",
					"dataSource": {
						"id": 214,
						"documentId": 22970
					}
				}
			]
		}
	],
	"meta": {
		"pagination": {
			"total": 1,
			"totalPages": 1,
			"currentPage": 1,
			"perPage": 10,
			"count": 1
		}
	}
}  
```

2. **Postpaid-MNP Example:**

```
{
	"data": [
		{
			"documentUuid": "f44d0a30-b28f-4641-854c-4bc50c7d7e56",
			"id": 22960,
			"instanceId": 47,
			"bizPartnerId": 87612478,
			"bizPartnerCountry": 384,
			"bizPartnerExternalRefId": "XZ876765-S33",
			"bizPartner": {
				"name": "Business Partner Example 1",
				"briefName": "BP 1",
				"partnerType": "Wholesale",
				"attn": "",
				"address": "",
				"post": "",
				"city": "",
				"vatNumber": "",
				"customAttributes": [
					{
						"codeName": "OBJECT_EXAMPLE",
						"value": {
							"propertyA": "value A",
							"propertyB": "value B"
						}
					}
				]
			},
			"documentDate": "2019-09-30",
            "deliveryDate": "2019-09-30",
            "documentNumber": "300919-1",
            "documentNumberMask": "300919-%d",
            "documentNumberNum": 1,
            "dueDate": "2019-10-30",
            "periodStart": "2019-09-01",
            "periodEnd": "2019-09-30",
            "currency": 978,
            "currencyCode": "EUR",
            "amountNoVat": 0.55,
            "amountVat": 0.55,
            "vatPercent": 0,
            "vat": 0,
            "rounding": 0,
            "total": 0.55,
            "totalUnpaid": 0.55,
            "totalPaid": 0,
            "domesticCurrency": 752,
            "domesticCurrencyCode": "SEK",
            "domesticCurrencyRate": 10.7287,
            "domesticAmountNoVat": 5.9,
            "domesticAmountVat": 5.9,
            "domesticRounding": 0,
            "domesticTotal": 5.9,
            "status": "approved",
            "insertDt": "2019-10-01T11:08:59Z",
            "statusDt": "2019-10-01T16:33:05Z",
            "paymentStatus": "open",
            "paymentStatusDate": "2019-10-01T16:33:05Z",
			"domainId": 2,
			"domainCodeName": "BULK-MNP",
			"documentClassCodeName": "CUSTOMER_INVOICE",
			"documentClassDomain": "invoice",
			"documentClassArea": "sales",
			"selfBilling": "no",
			"dataSourceId": 8,
			"dataSourceCodeName": "POSTPAID",
			"dataSourceSelector": "",
			"dataSource": {
				"id": 6363,
				"billingTotalBalance": {
					"id": 1994,
                    "instanceId": 12,
                    "bizPartnerId": 87612478,
                    "currency": 978,
                    "currencyCode": "EUR",
                    "billingTypeCodeName": "POSTPAID",
                    "name": "BP1 postpaid CHF",
                    "customAttributes": [
                        {
                            "codeName": "CONTRACT_NAME",
                            "value": "DD2000018"
                        }
                    ]
				}
			},
			"lang": "en",
			"documentType": 234,
			"documentTypeName": "MNP Bulk Invoice - Postpaid",
			"syncStatus": "none",
			"syncStatusDt": null,
			"disputeStatus": "none",
			"docsDeliveryStatus": "none",
			"docsDeliveryStatusDate": null,
			"items": [
				{
					"id": 99090,
                    "documentId": 22960,
                    "ordNum": 1,
                    "name": "Account: DIR",
                    "quantity": 12,
                    "measureUnit": "PIECE",
                    "price": 0,
                    "totalNoVat": 0.552,
                    "totalVat": 0.552,
					"dataSourceId": 8,
					"dataSourceCodeName": "POSTPAID",
					"dataSourceForeignKey": 45684,
					"dataSourceSelector": "",
					"dataSource": {
						"id": 13,
						"billingAccount": {
							"id": 3369,
                            "instanceId": 12,
                            "bizPartnerId": 87612478,
                            "currency": 978,
                            "currencyCode": "EUR",
                            "billingTypeCodeName": "POSTPAID",
                            "name": "DIR",
							"customAttributes": [
								{
									"codeName": "STRING_EXAMPLE",
									"value": "value C"
								}
							],
							"mnpConnections": [
								{
									"id": 17,
									"instanceId": 12,
									"name": "DIR",
									"authName": "7987823_DIR",
									"protocol": "HTTP"
								}
							]
						}
					}
				}
			]
		}
	],
	"meta": {
		"pagination": {
			"total": 1,
			"totalPages": 1,
			"currentPage": 1,
			"perPage": 10,
			"count": 1
		}
	}
}
```

3. **Postpaid-SMS Example:**

```
{
	"data": [
		{
			"documentUuid": "f44d0a30-b28f-4641-854c-4bc50c7d7e56",
			"id": 22960,
			"instanceId": 47,
			"bizPartnerId": 87612478,
			"bizPartnerCountry": 384,
			"bizPartnerExternalRefId": "XZ876765-S33",
			"bizPartner": {
				"name": "Business Partner Example 1",
				"briefName": "BP 1",
				"partnerType": "Wholesale",
				"attn": "",
				"address": "",
				"post": "",
				"city": "",
				"vatNumber": "",
				"customAttributes": [
					{
						"codeName": "OBJECT_EXAMPLE",
						"value": {
							"propertyA": "value A",
							"propertyB": "value B"
						}
					}
				]
			},
			"documentDate": "2019-09-30",
			"deliveryDate": "2019-09-30",
			"documentNumber": "300919-1",
			"documentNumberMask": "300919-%d",
			"documentNumberNum": 1,
			"dueDate": "2019-10-30",
			"periodStart": "2019-09-01",
			"periodEnd": "2019-09-30",
			"currency": 978,
			"currencyCode": "EUR",
			"amountNoVat": 0.55,
			"amountVat": 0.55,
			"vatPercent": 0,
			"vat": 0,
			"rounding": 0,
			"total": 0.55,
			"totalUnpaid": 0.55,
			"totalPaid": 0,
			"domesticCurrency": 752,
			"domesticCurrencyCode": "SEK",
			"domesticCurrencyRate": 10.7287,
			"domesticAmountNoVat": 5.9,
			"domesticAmountVat": 5.9,
			"domesticRounding": 0,
			"domesticTotal": 5.9,
			"status": "approved",
			"insertDt": "2019-10-01T11:08:59Z",
			"statusDt": "2019-10-01T16:33:05Z",
			"paymentStatus": "open",
			"paymentStatusDate": "2019-10-01T16:33:05Z",
			"domainId": 1,
			"domainCodeName": "BULK",
			"documentClassCodeName": "CUSTOMER_INVOICE",
			"documentClassDomain": "invoice",
			"documentClassArea": "sales",
			"selfBilling": "no",
			"dataSourceId": 2,
			"dataSourceCodeName": "POSTPAID",
			"dataSourceSelector": "",
			"dataSource": {
				"id": 6363,
				"billingTotalBalance": {
					"id": 1994,
					"instanceId": 12,
					"bizPartnerId": 87612478,
					"currency": 978,
					"currencyCode": "EUR",
					"billingTypeCodeName": "POSTPAID",
					"name": "BP1 postpaid CHF",
					"customAttributes": [
						{
							"codeName": "CONTRACT_NAME",
							"value": "DD2000018"
						}
					]
				}
			},
			"lang": "en",
			"documentType": 5,
			"documentTypeName": "Bulk Invoice",
			"syncStatus": "none",
			"syncStatusDt": null,
			"disputeStatus": "none",
			"docsDeliveryStatus": "none",
			"docsDeliveryStatusDate": null,
			"items": [
				{
					"id": 99090,
					"documentId": 22960,
					"ordNum": 1,
					"name": "Account: DIR",
					"quantity": 12,
					"measureUnit": "PIECE",
					"price": 0,
					"totalNoVat": 0.552,
					"totalVat": 0.552,
					"dataSourceId": 2,
					"dataSourceCodeName": "POSTPAID",
					"dataSourceForeignKey": 45684,
					"dataSourceSelector": "",
					"dataSource": {
						"id": 45684,
						"billingAccount": {
							"id": 3369,
							"instanceId": 12,
							"bizPartnerId": 87612478,
							"currency": 978,
							"currencyCode": "EUR",
							"billingTypeCodeName": "POSTPAID",
							"name": "DIR",
							"customAttributes": [
								{
									"codeName": "STRING_EXAMPLE",
									"value": "value C"
								}
							],
							"smsConnections": [
								{
									"id": 12023,
									"instanceId": 12,
									"name": "DIR",
									"authName": "7987823_DIR",
									"protocol": "SMPP"
								}
							]
						}
					}
				}
			]
		}
	],
	"meta": {
		"pagination": {
			"total": 1,
			"totalPages": 1,
			"currentPage": 1,
			"perPage": 10,
			"count": 1
		}
	}
}
```

4. **Prepaid Example**: 

```
{
	"data": [
		{
			"documentUuid": "f44d0a30-b28f-4641-854c-4bc50c7d7e56",
            "id": 22960,
            "instanceId": 41,
            "bizPartnerId": 87612478,
            "bizPartnerCountry": 384,
            "bizPartnerExternalRefId": "XZ876765-S33",
			"bizPartner": {
				"name": "Business Partner Example 1",
                "briefName": "BP 1",
                "partnerType": "wholesale",
                "attn": "",
                "address": "",
                "post": "",
                "city": "",
                "vatNumber": "",
                "customAttributes": [
                    {
                        "codeName": "OBJECT_EXAMPLE",
                        "value": {
                            "propertyA": "value A",
                            "propertyB": "value B"
                        }
                    }
                ]
			},
			"documentDate": "2019-09-30",
            "deliveryDate": "2019-09-30",
            "documentNumber": "300919-1",
            "documentNumberMask": "300919-%d",
            "documentNumberNum": 1,
            "dueDate": "2019-10-30",
            "periodStart": "2019-09-01",
            "periodEnd": "2019-09-30",
            "currency": 978,
            "currencyCode": "EUR",
            "amountNoVat": 0.55,
            "amountVat": 0.55,
            "vatPercent": 0,
            "vat": 0,
            "rounding": 0,
            "total": 0.55,
            "totalUnpaid": 0.55,
            "totalPaid": 0,
            "domesticCurrency": 752,
            "domesticCurrencyCode": "SEK",
            "domesticCurrencyRate": 10.7287,
            "domesticAmountNoVat": 5.9,
            "domesticAmountVat": 5.9,
            "domesticRounding": 0,
            "domesticTotal": 5.9,
            "status": "approved",
            "insertDt": "2019-10-01T11:08:59Z",
            "statusDt": "2019-10-01T16:33:05Z",
            "paymentStatus": "open",
            "paymentStatusDate": "2019-10-01T16:33:05Z",
            "domainId": 1,
            "domainCodeName": "BULK",
            "documentClassCodeName": "CUSTOMER_INVOICE",
            "documentClassDomain": "invoice",
            "documentClassArea": "sales",
            "selfBilling": "no",
			"dataSourceId": 1,
			"dataSourceCodeName": "PREPAID",
			"dataSourceSelector": "",
			"dataSource": {
				"id": 217,
				"billingTotalBalance": {
					"id": 1995,
					"instanceId": 12,
					"bizPartnerId": 87612478,
					"currency": 978,
					"currencyCode": "EUR",
					"billingTypeCodeName": "PREPAID",
					"name": "BP1 prepaid EUR",
					"customAttributes": [
                        {
                            "codeName": "CONTRACT_NAME",
                            "value": "DD2000018"
                        }
                    ]
				}
			},
			"lang": "en",
			"documentType": 19,
			"documentTypeName": "Bulk Invoice - Prepaid",
			"syncStatus": "none",
			"syncStatusDt": null,
			"disputeStatus": "none",
			"docsDeliveryStatus": "none",
			"docsDeliveryStatusDate": null,
			"items": [
				{
					"id": 99095,
					"documentId": 22960,
					"ordNum": 1,
					"name": "Clearing Test InvoiceItem",
					"quantity": 1,
					"measureUnit": "PIECE",
					"price": 1000,
					"totalNoVat": 1000,
					"totalVat": 1000,
					"dataSourceId": 0,
					"dataSourceCodeName": "",
					"dataSourceForeignKey": 0,
					"dataSourceSelector": "",
					"dataSource": null
				}
			]
		}
	],
	"meta": {
		"pagination": {
			"total": 1,
			"totalPages": 1,
			"currentPage": 1,
			"perPage": 10,
			"count": 1
		}
	}
}
```
