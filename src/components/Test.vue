<template>

<div>
  <h1>Claim Request Content form</h1>
<el-dialog
  title="Tips"
  :visible.sync="dialogVisible"
  width="30%">
  
  <p> First Name:{{ ruleForm.FirstName }}</p>
   <p> First Name:{{ ruleForm.LastName }}</p>
    <p> Emial:{{ ruleForm.Email }}</p>
    <p> SubjectTitle:{{ ruleForm.SubjectTitle }}</p>
    <p>Claim Description: {{ ruleForm.desc}}</p>
    <p>Claim Request Content form: true</p>
    
  <span>This is a message</span>

</el-dialog>
  <el-form
    :model="ruleForm"
    :rules="rules"
    v-show="!dialogVisible"
    ref="ruleForm"
    label-width="120px"
    class="demo-ruleForm"
  >
    <el-form-item label="First Name" prop="FirstName">
      <el-input v-model="ruleForm.FirstName"></el-input>
    </el-form-item>
    <el-form-item label="Last Name" prop="LastName">
      <el-input v-model="ruleForm.LastName"></el-input>
    </el-form-item>
    <el-form-item label="Email" prop="Email">
      <el-input v-model="ruleForm.Email"></el-input>
    </el-form-item>
    <el-form-item label="Subject Title" prop="SubjectTitle">
      <el-input v-model="ruleForm.SubjectTitle"></el-input>
    </el-form-item>
    <el-form-item label="Claim Request Content form" prop="desc">
      <el-input type="textarea" v-model="ruleForm.desc"></el-input>
    </el-form-item>
    <el-form-item label="" prop="type">
      <el-checkbox v-model="ruleForm.type">Agreement</el-checkbox>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm('ruleForm')">Create</el-button>

    </el-form-item>
  </el-form>
  </div>
</template>




<script>
export default {
  data() {
    return {
      dialogVisible: false,
      ruleForm: {
        FirstName: "",
        LastName: "",
        Email: "",
        SubjectTitle: "",
        desc: "",
        type:[],
        showErrorChecked: false
      },
      rules: {
        FirstName: [
          {
            required: true,
            message: "Please input first name",
            trigger: "blur"
          },
          {
            min: 3,
            max: 5,
            message: "Length should be 3 to 5",
            trigger: "blur"
          }
        ],
        LastName: [
          {
            required: true,
            message: "Please input last name",
            trigger: "blur"
          },
          {
            min: 3,
            max: 5,
            message: "Length should be 3 to 5",
            trigger: "blur"
          }
        ],
        Email: [
          {
            required: true,
            message: "Please input your email",
            trigger: "blur"
          },
          {
            min: 5,
            max: 20,
            message: "Length should be 5 to 20",
            trigger: "blur"
          }
        ],
        SubjectTitle: [
          {
            required: true,
            message: "Please input your SubjectTitle",
            trigger: "blur"
          },
          {
            min: 5,
            max: 30,
            message: "Length should be 5 to 20",
            trigger: "blur"
          }
        ],
        desc: [
          {
            required: true,
            message: "Please input Claim Request Content form",
            trigger: "blur"
          }
        ],
        type: [
            { type: 'array', required: true, message: 'Please select at least one activity type', trigger: 'change' }
          ]
      }
    };
  },
  methods: {
    submitForm(formName) {
    
      this.$refs[formName].validate(valid => {
        if (valid) {
           this.dialogVisible = true;
         
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>