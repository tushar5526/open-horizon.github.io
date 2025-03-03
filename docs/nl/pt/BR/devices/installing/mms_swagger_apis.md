{
    "swagger": "2.0",
  "info": {
      "description": "This documentation is for the Policy resource for IBM Multicloud Manager (policy.mcm.ibm.com).\nThe IBM Multicloud Manager Policy resource has four possible requests: create, query all policies, query a single policy, and delete.",
      "version": "3.2.1",
      "title": "IBM Multicloud Manager policy API Documentation",
      "termsOfService": "http://swagger.io/terms/",
      "contact": {
        "email": "apiteam@swagger.io"
      },
      "license": {
        "name": "Apache 2.0",
        "url": "http://www.apache.org/licenses/LICENSE-2.0.html"
      }
    },
    "basePath": "/kubernetes/apis",
    "tags": [
      {
        "name": "Policy.mcm.ibm.com",
        "description": "Create and manage policies with the policy resource."
      }
    ],
    "schemes": [
      "https",
      "http"
    ],
    "paths": {
      "/policy.mcm.ibm.com/v1alpha1/namespaces/{namespace}/policies": {
        "post": {
          "tags": [
            "Policy.mcm.ibm.com"
          ],
          "summary": "Create a policy",
          "description": "Create a policy to report and validate cluster governance and risk.",
          "operationId": "createPolicy",
          "consumes": [
            "application/yaml"
          ],
          "parameters": [
            {
              "in": "body",
              "name": "body",
              "description": "Parameters describing the policy to be created.",
              "required": true,
              "schema": {
                "$ref": "#/definitions/Policy"
              }
            },
            {
              "in": "path",
              "name": "namespace",
              "description": "Namespace that you want to use, for example, default.",
              "required": true,
              "type": "string"
            },
            {
              "name": "COOKIE",
              "in": "header",
              "description": "Authorization: Bearer {ACCESS_TOKEN} ; ACCESS_TOKEN is the user access token.",
              "type": "string",
              "required": true
            }
          ],
          "responses": {
            "200": {
              "description": "Success"
            },
            "403": {
              "description": "Access forbidden"
            },
            "404": {
              "description": "Resource not found"
            },
            "500": {
              "description": "Internal service error"
            },
            "503": {
              "description": "Service unavailable"
            }
          }
        },
        "get": {
          "tags": [
            "Policy.mcm.ibm.com"
          ],
          "summary": "Query all policies",
          "description": "Query your policies for more details.",
          "operationId": "queryPolicies",
          "consumes": [
            "application/yaml"
          ],
          "parameters": [
            {
              "in": "path",
              "name": "namespace",
              "description": "Namespace that you want to use, for example, default.",
              "required": true,
              "type": "string"
            },
            {
              "name": "COOKIE",
              "in": "header",
              "description": "Authorization: Bearer {ACCESS_TOKEN} ; ACCESS_TOKEN is the user access token.",
              "type": "string",
              "required": true
            }
          ],
          "responses": {
            "200": {
              "description": "Success"
            },
            "403": {
              "description": "Access forbidden"
            },
            "404": {
              "description": "Resource not found"
            },
            "500": {
              "description": "Internal service error"
            },
            "503": {
              "description": "Service unavailable"
            }
          }
        }
      },
      "/policy.mcm.ibm.com/v1alpha1/namespaces/{namespace}/policies/{policy_name}": {
        "get": {
          "tags": [
            "Policy.mcm.ibm.com"
          ],
          "summary": "Query a single policy",
          "description": "Query a single policy for more details.",
          "operationId": "queryPolicy",
          "parameters": [
            {
              "name": "policy_name",
              "in": "path",
              "description": "Name of the policy that you wan to query.",
              "required": true,
              "type": "string"
            },
            {
              "in": "path",
              "name": "namespace",
              "description": "Namespace that you want to use, for example, default.",
              "required": true,
              "type": "string"
            },
            {
              "name": "COOKIE",
              "in": "header",
              "description": "Authorization: Bearer {ACCESS_TOKEN} ; ACCESS_TOKEN is the user access token.",
              "type": "string",
              "required": true
            }
          ],
          "responses": {
            "200": {
              "description": "Success"
            },
            "403": {
              "description": "Access forbidden"
            },
            "404": {
              "description": "Resource not found"
            },
            "500": {
              "description": "Internal service error"
            },
            "503": {
              "description": "Service unavailable"
            }
          }
        },
        "delete": {
          "tags": [
            "Policy.mcm.ibm.com"
          ],
          "summary": "Delete a policy",
          "description": "",
          "operationId": "deletePolicy",
          "parameters": [
            {
              "name": "policy_name",
              "in": "path",
              "description": "Name of the policy that you want to delete.",
              "required": true,
              "type": "string"
            },
            {
              "in": "path",
              "name": "namespace",
              "description": "Namespace that you want to use, for example, default.",
              "required": true,
              "type": "string"
            },
            {
              "name": "COOKIE",
              "in": "header",
              "description": "Authorization: Bearer {ACCESS_TOKEN} ; ACCESS_TOKEN is the user access token.",
              "type": "string",
              "required": true
            }
          ],
          "responses": {
            "200": {
              "description": "Success"
            },
            "403": {
              "description": "Access forbidden"
            },
            "404": {
              "description": "Resource not found"
            },
            "500": {
              "description": "Internal service error"
            },
            "503": {
              "description": "Service unavailable"
            }
          }
        }
      }
    },
    "definitions": {
      "Policy": {
        "type": "object",
        "required": [
          "apiVersion",
          "kind",
          "metadata",
          "spec"
        ],
        "properties": {
          "apiVersion": {
            "type":"string"
          },
          "kind": {
            "type":"string"
          },
          "metadata": {
            "type": "object"
          }, "spec": {
            "type": "object",
            "properties": {
              "remediationAction": {
                "type":"string"
              },
              "namespaces": {
                "type": "object",
                "properties": {
                  "include": {
                    "type": "array",
                    "items": {
                      "type": "string"
                    }
                  },
                  "exclude": {
                    "type": "array",
                    "items": {
                      "type": "string"
                    }
                  }
                }
              },
              "roleTemplates": {
                "type": "object",
                "properties": {
                  "kind": {
                    "type":"string"
                  },
                  "apiVersion": {
                    "type":"string"
                  },
                  "complianceType": {
                    "type":"string"
                  },
                  "metadata": {
                    "type": "object"
                  },
                  "selector": {
                    "type": "object",
                    "properties": {
                      "matchLabels": {
                        "type": "object"
                      }
                    }
                  },
                  "rules": {
                    "type": "array",
                    "items": {
                      "type": "object",
                      "properties": {
                        "complianceType": {
                          "type":"string"
                        },
                        "PolicyRule": {
                          "type": "object",
                          "properties": {
                            "apiGroups": {
                              "type": "array",
                              "items": {
                                "type": "string"
                              }
                            },
                            "resources": {
                              "type": "array",
                              "items": {
                                "type": "string"
                              }
                            },
                            "verbs": {
                              "type": "array",
                              "items": {
                                "type": "string"
                              }
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
          }
        },
        "example": {
          "apiVersion": "policy.mcm.ibm.com/v1alpha1",
          "kind": "Policy",
          "metadata": {
            "name": "test-policy-swagger",
            "description": "Example API Swagger content for the Policy resource."
          }, "spec": {
            "remediationAction": "enforce",
            "namespaces": {
              "include": [
                "default"
              ],
              "exclude": [
                "kube*"
              ]
            },
            "roleTemplates": {
              "kind": "RoleTemplate",
              "apiVersion": "roletemplate.mcm.ibm.com/v1alpha1",
              "complianceType": "musthave",
              "metadata": {
                "namespace": null,
                "name": "test-role"
              },
              "selector": {
                "matchLabels": {
                  "cloud": "IBM"
                }
              }
            },
            "rules": [
              {
                "complianceType": "musthave",
                "PolicyRule": {
                  "apiGroups": [
                    "extensions",
                    "apps"
                  ],
                  "resources": [
                    "deployments"
                  ],
                  "verbs": [
                    "get",
                    "list",
                    "watch",
                    "delete"
                  ]
                }
              },
              {
                "complianceType": "mustnothave",
                "PolicyRule": {
                  "apiGroups": [
                    "core"
                  ],
                  "resources": [
                    "pods"
                  ],
                  "verbs": [
                    "create",
                    "update",
                    "patch"
                  ]
                }
              },
              {
                "PolicyRule": null,
                "apiGroups": [
                  "core"
                ],
                "resources": [
                  "secrets"
                ],
                "verbs": [
                  "get",
                  "watch",
                  "list",
                  "create",
                  "delete",
                  "update",
                  "patchß"
                ]
              }
            ]
          }
        }
      }
    },
    "externalDocs": {
      "description": "Find out more about Swagger."
    },
    "url": "http://swagger.io"
  }
